# 環境配置

1. 在屬性->C/C++->代碼生成->運行庫下，將**多線程DLL(/MD)** 改為**多線程(/MT)**。
2. 在屬性->C/C++->常規->附加包含目錄下，將**包含頭文件的目錄**添加進去。
3. 在屬性->鏈接器->常規->附加庫目錄下，將**包含lib文件的目錄**添加進去。
4. 在屬性->鏈接器->輸入->附加依賴項下，將需要包含的**lib文件名**添加進去。
5. 將所有需要包含的DLL文件複製到工程目錄下。

# SDL窗口創建

首先包含所需文件，並在`mian`中初始化。因為`SDL.h`中包含以下聲明`#define mian SDL_main`，所以需要在文件中包含代碼`#define SDL_MAIN_HANDLED`才能讓我們寫的`main`不做為`SDL_main`運行。

``` C++
#define SDL_MAIN_HANDLED

#include <SDL.h>
#include <SDL_ttf.h>
#include <SDL_mixer.h>
#include <SDL_image.h>
#include <SDL2_gfxPrimitives.h>

/*--- main func ---*/

SDL_Init(SDL_INIT_EVERYTHING);
IMG_Init(IMG_INIT_JPG | IMG_INIT_PNG);
Mix_Init(MIX_INIT_MP3);
TTF_Init();

Mix_OpenAudio(44100, MIX_DEFAULT_FORMAT, 2, 2048);
```

創建窗口、事件處理器與主循環：

``` C++
SDL_Window* window = SDL_CreateWindow(u8"Demo編碼窗口測試", SDL_WINDOWPOS_CENTERED, SDL_WINDOWPOS_CENTERED, 1280, 720, SDL_WINDOW_SHOWN);
SDL_Renderer* renderer = SDL_CreateRenderer(window, -1, SDL_RENDERER_ACCELERATED);

SDL_Event event;

bool is_quit = false;
while(!is_quit){
	while (SDL_PollEvent(&event)) {
		switch (event.type) {
		case SDL_QUIT:
			is_quit = true;
		default:
			break;
		}
	}
	
	// Clean the screen
	SDL_SetRenderDrawColor(renderer, 0, 0, 0, 255);
	SDL_RenderClear(renderer);

	// Handle the graphics
	SDL_RenderPresent(renderer);
}
```

# SDL創建圖片

``` C++
SDL_Surface* suf_image = IMG_Load("avatar.jpg");
SDL_Texture* tex_image = SDL_CreateTextureFromSurface(renderer, suf_image);

SDL_Rect rect_img;
rect_img.x = 100;
rect_img.y = 100;
rect_img.w = suf_image->w;
rect_img.h = suf_image->h;

/*--- 主循環中 ---*/

// Handle the graphics
SDL_RenderCopy(renderer, tex_image, nullptr, &rect_img);
SDL_RenderPresent(renderer);
```

# SDL應用字體

``` C++
TTF_Font* font = TTF_OpenFont("ipix.ttf", 32);
SDL_Color color = { 255, 255, 255, 255 };
SDL_Surface* suf_text = TTF_RenderUTF8_Blended(font, u8"Demo编码字体测试", color);
SDL_Texture* tex_text = SDL_CreateTextureFromSurface(renderer, suf_text);

SDL_Rect rect_text;
rect_text.x = 100;
rect_text.y = 100;
rect_text.w = suf_text->w;
rect_text.h = suf_text->h;

/*--- 主循環中 ---*/

// Handle the graphics
SDL_RenderCopy(renderer, tex_text, nullptr, &rect_text);
```

# SDL撥放音樂

``` C++
Mix_Music* music = Mix_LoadMUS("music.mp3");
Mix_FadeInMusic(music, -1, 1500);
```

# SDL繪製圓形

``` C++
/*--- 主循環中 ---*/

// Handle the graphics
filledCircleRGBA(renderer, pos_cursor.x, pos_cursor.y, 50, 255, 0, 0, 128);
```

# SDL固定幀數

``` C++
int fps = 165;
Uint64 last_counter = SDL_GetPerformanceCounter();
Uint64 counter_freq = SDL_GetPerformanceFrequency();

/*--- 主循環中 ---*/
Uint64 current_counter = SDL_GetPerformanceCounter();
double delta = (double)(current_counter - last_counter) / counter_freq;
last_counter = current_counter;
if (delta * 1000 < 1000.0 / fps)
	SDL_Delay((Uint32)(1000.0 / fps - delta * 1000));
```