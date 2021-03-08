
1. ### error TS2705: An async function or method in ES5/ES3 requires the 'Promise' constructor.
tsconfig.json 파일에  "lib": ["es2015"],  를 설정해 주자.
target이 es5로 잡혀있을텐데 얘도 지정해 줘야한다.

<br><br>

2. ### error TS7006: Parameter 'any' implicitly has an 'any' type
tsconfig.json 파일에 "noImplicitAny": true,  로 비활성화 되어있을텐데 "noImplicitAny": false,  로 활성화 시켜주자.

<br><br>

3. ### TypeError: Unexpected MODIFIER at 1, expected END
이게 뭔 말이냐면 es5에서 nextscript로 버전 업그레이드 하면서 주소 지정 형식이 바꼈음 <br>
(난 지금 typescript 쓰지만 어쨌든 es5보다 상위니까 해당됨)
<br><br>
index.ts 에서 라우터부분의 <br>
router.get('/*', async (ctx) => {
    ctx.body = 'Hello World!';
});
<br>

이렇게 하는게 있을거임

router.get('(/*)', async (ctx) => {
    ctx.body = 'Hello World!';
});
<br>
그냥 이렇게 주소 지정할때 소괄호 해주면 됨 아 진짜 

<br><br>

4. ### 만약에 모듈을 새로 설치했는데 "모듈 또는 해당 형식 선언을 찾을 수 없습니다.ts 2307" 이런 오류와 함께 import 한 놈이 빨간줄 뜬다?

그거 버전안맞아서 그렇다. "npm uninstall 모듈이름" 해준다음에 다시 맞는 버전으로 설치해주자.

<br><br>

5. ### 만약 yarn start 해서 서버를 켰는데 [nodemon] app crashed - waiting for file changes before starting 이런 에러가 난다?

기존에 있던 서버가 안죽어서 그렇다. PID 확인 후 프로세스를  제거하자. <br>
netstat -ntlp <br>
kill pid <br>
로 죽여도 되고, 작업관리자 켜서 해당 nodejs서버 죽이면 된다.

<br><br>

6. ### Error: Cannot find module

이렇게 뜬다면 대체로 node .\src\틀린이름 <br>
이런식으로 이름이나 경로가 틀려서 그런거 다시 한번 

<br><br>

7. ### yarn : 이 시스템에서 스크립트를 실행할 수 없으므로  C:\Users~~~ 파일을 로드할 수 없습니다.
yarn 실행하려는데 <br>
이러면 이거 권한 문제이다. <br>
관리자 권한으로 powershell 킨다음에 <br>
 <br>
해결책  <br>
1. 관리자 권한으로 power shell 실행  <br>
2. Get-ExecutionPolicy 명령어를 입력하면 권한 상태가 보여짐  <br>
3. RemoteSigned의 권한이 아니라면 Set-ExecutionPolicy RemoteSigned 입력  <br>
4. 변경하시겠습니까? Y  <br>
5. 2번 내용 다시 입력하면 RemoteSigned으로 변경된 것을 확인 할 수 있다.  <br>
그래서 yarn을 잘 설치했습니다!  <br>

 <br> <br>
 
 8. ### The project was not built since its build path is incomplete. Cannot find the class file for ... 오류발생시 해결방법

 마븐 업데이트가 제대로 안된거다 .m의 repository 폴더를 지우고 다시 마븐을 
출처: https://papababo.tistory.com/entry/The-project-was-not-built-since-its-build-path-is-incomplete-Cannot-find-the-class-file-for-오류발생시-해결방법 참고


<br><br>

9. ### [WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!

마븐 인스톨했는데 이런 문구가 나온다면 pom.xml의 <properties>설정 사이에 다음과 같은 설정값을 추가한다. <br><br>

 <!-- Build Encoding UTF-8 Setting -->
 <properties>
  <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
  <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
 </properties>
 
 
