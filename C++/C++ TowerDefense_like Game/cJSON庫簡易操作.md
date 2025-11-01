``` C++
#include <cJSON>

void test_json() {
	std::ifstream file("test.json");
	if (!file.good()) {
		std::cout << "Cannot open test.json" << std::endl;
		return;
	}

	std::stringstream str_stream;
	str_stream << file.rdbuf();
	file.close();

	cJSON* json_root = cJSON_Parse(str_stream.str().c_str());

	cJSON* json_name = cJSON_GetObjectItem(json_root, "name");
	cJSON* json_age = cJSON_GetObjectItem(json_root, "age");
	cJSON* json_pets = cJSON_GetObjectItem(json_root, "pets");

	std::cout << json_name->string << ": " << json_name->valuestring << std::endl;
	std::cout << json_age->string << ": " << json_age->valueint << std::endl;
	std::cout << json_pets->string << ": " << std::endl;

	cJSON* json_item = nullptr;
	cJSON_ArrayForEach(json_item, json_pets) {
		std::cout << "\t" << json_item->valuestring << std::endl;
	}
}
```