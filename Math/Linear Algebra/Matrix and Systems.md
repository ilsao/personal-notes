
Assume $\vec{u} = (u_{1}, u_{1}\dots u_{n})$ and $\vec{v}= (v_{1}, v_{2} \dots v_{n})$ are two solutions of $a_{1}x_{1}+a_{2}x_{2}+ \dots +a_{n}x_{n}=b$. **Prove** that for any real number $C$, $\vec{u}+c(u-v)$ is the solution of $a_{1}x_{1}+a_{2}x_{2}+ \dots +a_{n}x_{n}=b$. 

Sol 1:

$\because$ We have $a_{1}u_{1}+a_{2}u_{2}+ \dots a_{n}u_{n} = b$ and $a_{1}v_{1}+a_{2}v_{2}+ \dots +a_{n}v_{n} = b$ 
$\therefore$ We have $a_{1}(u_{1}-v_{1})+a_{2}(u_{2}-v_{2})+ \dots +a_{n}(u_{n}-v_{n})=0$. i.e., $\vec{u}-\vec{v}$ is one of the solution of $a_{1}x_{1}+a_{2}x_{2}+\dots+a_{n}x_{n}=0$.
$\implies$ $c(\vec{u}-\vec{v})$ is also the one of the solution of $a_{1}x_{1}+a_{2}x_{2}+\dots+a_{n}x_{n}=0$. 
Then, we add $\vec{u}$ to $c(\vec{u}-\vec{v})$. i.e., $\vec{u} + c(\vec{u}-\vec{v})$, it's the solution of $a_{1}x_{1}+a_{2}x_{2}+ \dots +a_{n}x_{n}=b$. 

Sol 2:

$a⋅(u+c(u−v))=a⋅u+c(a⋅u−a⋅v)=b+c(b−b)=b$.

# Row Echelon Form (REF)

1. The first nonzero entry in each nonzero row is 1.
2. If row $k$ does not consist entirely of zeros, the number of leading zero entries in row $k+1$ is greater than the number of leading zero entries in row $k$. 
3. If there are rows whose entires are zero,  they're below the rows having nonzero entries. 

The process of transform a matrix into REF is called **Guassian elimination**.

# Reduced Row Echelon Form (RREF)

If a system in row echelon form and all the entries above the leading 1 in each column have been eliminated, it's **reduced row echelon form**. 

1. The matrix is in row echelon form. 
2. The first nonzero entry in each row is the only nonzero entry in it's column

The process of transform a matrix into RREF is called **Gauss-Jordan reduction**.

# Overdetermined/Undetermined Systems

Overdetermined Systems: If there're **more** equations than unknows, it's an **overdetermined** system. 

Undetermined Systems: If there're **fewer** equations than unknows, it's an **undetermined** system. 

# Homogeneous Systems

A system of linear equations is said to be **homogeneous(齊次的)** if the constant on the right-hand side are all zero.

1. Homogeneous systems are always consistent. 
2. If an homogeneous system have an unique solution, it must be a trival solution = $(0, 0, \dots, 0)$. 
3. An $m \times n$ homogeneous system of linear equations has a nontrival solution if $m < n$. 

