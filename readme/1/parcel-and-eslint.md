# Parcel & ESLint

#### Parcel

Zero Configuration. 특별한 설정 없이 바로 사용 가능한 빌드 도구. 내부적으로 SWC를 사용해 기존 도구보다 빠르다.

#### 설정작업

```javascript
// package.json 파일에 source 속성 추가.
"source": "./index.html",
```

```javascript
// parcel-reporter-static-files-copy 패키지 설치 후 `.parcelrc` 파일 작성.
// 이렇게 하면 static 폴더의 파일을 정적 파일로 Serving할 수 있다(이미지 등 Assets).
{
  "extends": ["@parcel/config-default"],
  "reporters":  ["...", "parcel-reporter-static-files-copy"]
}
```

#### 빌드 + 정적 서버 실행

```
npx parcel build
npx servor ./dist
```

***

#### ESLint

무엇을 위해서?

* 스타일 통일
* 잠재적 문제 발견
* 베스트 프랙티스 추천 → 최신 트렌드를 학습하는데 활용할 수 있다.

[VS Code ESLint extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

`.vscode/settings.json`파일을 추가해 JS/TS 파일을 저장할 때마다 ESLint를 실행하고 문제점을 고치게 설정할 수 있다.

```javascript
{
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    }
}
```

#### 아샬이 쓰는 VS Code 기본 세팅

* [VS Code 기본 세팅](https://github.com/ahastudio/CodingLife/blob/main/20211008/react/.vscode/settings.json)
* [Trailing Spaces](https://marketplace.visualstudio.com/items?itemName=shardulm94.trailing-spaces)
