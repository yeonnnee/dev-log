# SSG와 SSR

***SSR 과 SSG의 차이는?**

- HTML 페이지를 언제 생성할 것인가의 차이
    - SSR: 각각의 요청마다 HTML 생성 (HTML 생성 후 데이터 fetch)
    - SSG: (프로덕션 모드에서만) HTML을 빌드 타임에 각 페이지별로 생성하고 해당 페이지로 요청이 올 경우 이미 생성된 HTML 문서를 반환한다. (fetched data와 함께 HTML 문서 반환)

![ssg.png](./ssg.png)

![ssr.png](./ssr.png)

- SSR → getServerSideProps 사용

```jsx
function Home(props) {
    return <List data={props.data} />;
}

export async function getServerSideProps(context) {
    const req = context.req;
    const res = context.res;

    const id = context.params.id; // params는 파일 or 폴더명에서 [id]으로 지정한 값 

    // fetch data from an API
    return {
        props: {
            data: ....
        },
        
    }	
}
```

- SSG → getStaticProps, getStaticPaths 사용

```jsx
function Home(props) {
    return <List data={props.data} />;
}

// dynamic page가 있고, getStaticProps를 사용했다면 아래 함수에 params 정의 필요. 
// why? > Next js는 dynamic page가 있다면 모든 dynamic page를 pre-generaged해야 한다. 
// getStaticProps는 build 타임에서 실행되기 때문에, pre-generated page를 들어가게 된다면 404 에러 발생할 것. 그래서 아래 함수에 url 정의
export async function getStaticPaths() {
    // describe all the dynamic segment values
    return {
        fallback: false, // false -> 정의되지않은 key값으로 url 진입시, 404 에러 
        paths: [
            { 
                params: {
                    keyName: value
                }
            }
        ]
    }

}

export async function getStaticProps() {
    // fetch data from an API
    return {
        props: {
            data: ....
        },
        revalidate: 10 // deployment 된 후 얼마나 규칙적으로 페이지를 업데이트 할 것인가 결정하는 옵션. 최댓값은 10
// 규칙적으로 update가 아니라 req있을 때마다 update 하고싶다? SSR 사용
    }	
}
```