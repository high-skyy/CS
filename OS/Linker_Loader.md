# Linkers and Loaders

## Roles of Compiler, Linker, Loader
![OS_Linker_Loader](https://user-images.githubusercontent.com/105041834/188276080-dba53fb9-8dd1-409d-a8f4-c8edb60c0013.JPG)
1. Source files are compiled into object files that are designed to be loaded into any physical memory location, a format known as an relocatable object file

> 해당 오브젝트 파일은 어셈블리어(기계어(0,1)와 일대일 대응이 되는 컴퓨터 프로그래밍의 저급 언어)로 되어 있다.
 
2. Next, the linker combines these relocatable object files into a single binary executable file. During the linking phase, other object files or libraries may be included as well, such as the standard C or math library

> 링커의 경우는 오브젝트 파일들을 실행 파일로 만들어 준다. (파일이 다른 파일에 있는 method를 호출하게 될 경우 등을 가능하게 해 주기 위해 파일을 합치는 역할을 한다.)

3. A loader is used to load the binary executable file into memory, where it is eligible to run on a CPU core.

> CPU는 Main memory에 있는 내용들만 가져다 사용할 수 있기 때문에 loader에 경우는 메모리에 실행 파일을 load 시켜 준다.

## References
[Reference](https://ko.wikipedia.org/wiki/%EC%96%B4%EC%85%88%EB%B8%94%EB%A6%AC%EC%96%B4#:~:text=%EA%B8%B0%EA%B3%84%EC%96%B4%EB%8A%94%20%EC%8B%A4%EC%A0%9C%EB%A1%9C%20%EC%BB%B4%ED%93%A8%ED%84%B0%EC%9D%98,%ED%95%9C%20%EA%B2%83%EC%9D%B4%20%EC%96%B4%EC%85%88%EB%B8%94%EB%A6%AC%20%EC%96%B8%EC%96%B4%EC%9D%B4%EB%8B%A4.)

Book : Operating System Concepts by Abraham Silberschatz, Greg Gagne, Peter B. Galvin
