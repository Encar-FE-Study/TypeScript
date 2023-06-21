# tsconfig.json란?

tsconfig.json은 타입스크립트를 자바스크립트로 변환 시키는 컴파일 설정을 한꺼번에 정의 해놓는 파일이라고 보면 된다. 프로젝트를 컴파일 하는데 필요한 루트 파일, 컴파일러 옵션 등을 상세히 설정할 수 있다.

```jsx
// 자주 쓰이는 tsconfig.json

{
	"compilerOptions": {
		"target": "es5",
		"lib": ["dom", "dom.iterable", "esnext"],
		"allowJs": true,
		"skipLibCheck": true,
		"strict": true,
		"forceConsistentCasingInFileNames": true,
		"noEmit": true,
		"esModuleInterop": true,
		"module": "esnext",
		"moduleResolution": "node",
		"resolveJsonModule": true,
		"isolatedModules": true,
		"jsx": "preserve",
		"incremental": true,
		"strictNullChecks": true
	},
	"include": ["**/*.ts", "**/*.tsx"],
	"exclude": ["node_modules"]
}
```

# ****tsconfig 전역 속성****

tsconfig 전역 속성이란, 파일의 최상위에 위치하고 있는 속성들을 일컫는다.

```jsx
{
    // TypeScript 컴파일러의 옵션들을 지정하는 속성
    "compilerOptions": { 
        "target": "es5", 
        "module": "commonjs", 
        "strict": true, 
        "sourceMap": true
        // ... 무수히 많은 속성들
    },

    // 컴파일할 파일들의 개별 목록을 지정하는 속성
    "files": ["src/main.ts", "src/utils.ts"],

    // 컴파일할 파일들을 지정하는 속성 (와일드 카드 패턴으로 묶어 표현) 
    "include": [ "src/**/*.ts" ], 
    
    // 컴파일 대상에서 제외할 파일들을 지정하는 속성 
    "exclude": [ "node_modules", "**/*.test.ts" ], 
    
    // 다른 tsconfig.json 파일을 상속받아서 설정을 재사용할 수 있게 해주는 속성 
    "extends": "./configs/base.json", 
}
```

## **files**

프로젝트에서 컴파일할 파일들의 목록을 명시적으로 지정하는 속성이다.

files 속성은 밑에서 배울 exclude보다 우선순위가 높다. 만일 이 속성이 생략되면 include와 exclude 속성으로 컴파일 대상을 결정한다.

```jsx
{
  "files": [ // 파일 확장자까지 정확히 작성해줘야 한다
    "src/main.ts",
    "src/utils.ts",
    "src/types.d.ts"
  ]
}
```

## **extends**

extends는 다른 tsconfig.json 파일의 설정들을 가져와 재사용할 수 있게 해주는 옵션이다. 보통 extends 속성은 tsconfig.json 파일의 최상위에 위치한다.

예를들어 config/base.json 파일의 속성 설정을 현 tsconfig.json 파일에 포맷이 맞으면 base파일의 설정을 상속 받게 된다.

```jsx
// config/base.json
{
  "compilerOptions": {
    "noImplicitAny": true,
    "strictNullChecks": true
  }
}
```

```jsx
{
  "extends": "./configs/base",
  "compilerOptions": {
    "strictNullChecks": false
  },
  "files": [
    "src/main.ts",
    "src/utils.ts",
    "src/types.d.ts"
  ]
}
```

## **include**

include 속성은 files 속성과 같이 프로젝트에서 컴파일할 파일들을 지정하는 속성이지만, **와일드 카드** 패턴으로 지정한다는 점에서 차이가 있다. 또한 include는 files 속성과는 달리 exclude보다 약해 include에 명시되어 있어도 exclude에도 명시되어 있으면 제외 되게 된다.

```jsx
{
  "compilerOptions": {
    ...
  },
  "include": [
    "src/*.ts", // src 디렉토리에 있는 모든 .ts 파일
    "dist/test?.ts" // dist 디렉토리에 있는 test1.ts, test2.ts , test3.ts ..등에 일치
    "test/**/*.spec.ts" // test 디렉토리와 그 하위 디렉토리에 있는 모든 .spec.ts 파일
  ]
}
```

**와일드 카드 패턴**

👉 tsconfig.json 파일에서 include나 exclude 속성에 사용할 수 있는 파일이나 디렉토리를 그룹화하여 일치시키는 기호라고 보면 된다

- * : 해당 디렉토리에 있는 모든 파일
- ? : 해당 디렉토리에 있는 파일들의 이름 중 한 글자라도 포함하면 해당
- ** : 해당 디렉토리의 하위 디렉토리의 모든 파일을 포함

## **exclude**

exclude 속성은 프로젝트에서 컴파일 대상에서 제외할 파일들을 와일드카드 패턴으로 지정하는 속성이다. 즉, include의 반대 버전이라 보면 된다.

```jsx
{
  "compilerOptions": {
    ...
  },
  
  "exclude": [
    "node_modules", // node_modules 디렉토리를 제외
    "**/*.test.ts" // 모든 .test.ts 파일을 제외
  ]
}
```

## ****compilerOptions****

컴파일 대상 파일들을 어떻게 변환할지 세세히 정하는 옵션이다.

많은 옵션이 있지만 주로 쓰이는 옵션 위주로 정리해보았다.

### **target**

어떠한 버전의 JavaScript 코드로 컴파일 할지 지정한다. 자바스크립트 버전 지정 값을 넣지 않으면 default로 es5로 컴파일 된다.

target 프로퍼티는 lib 프로퍼티의 기본값도 자동으로 결정 시킨다.  따라서 target 프로퍼티와 lib 프로퍼티를 권장되는 방식대로 직접 맞출 수도 있지만, 편의를 위해 그냥 target 프로퍼티만 지정할 수도 있다.

target 프로퍼티 값중에 **ESNext** 옵션값이 있는데, 가장 최신 기능의 자바스크립트 버전을 가리키는 값이다. 이 설정은 주의 깊게 사용되어야 하는데, 왜냐하면 현재 TypeScript의 버전에 따라 ESNext가 가리키는 버전이 달라질 수 있기 때문이다.

```jsx
"compilerOptions": {
	"target": "ES6" // 어떤 버전의 자바스크립트로 컴파일 될 것인지 설정
    // 'es3', 'es5', 'es2015', 'es2016', 'es2017','es2018', 'esnext' 가능
}
```
<br/>

### **lib**
<br/>

프로젝트에서 사용할 라이브러리를 설정. **`dom`**과 **`dom.iterable`**은 DOM API를 사용할 수 있도록 지원하며, **`esnext`**는 ECMAScript의 최신 기능을 사용할 수 있도록 지원한다.

이 프로퍼티가 지정되어 있지 않다면 target 프로퍼티에 지정된 버전에 따라 필요한 타입 정의들에 대한 정보가 자동으로 지정된다.  예를 들어, target 프로퍼티가 ES6 혹은 그 이상의 버전으로 지정되었는데, lib 프로퍼티가 지정되지 않다면 자동으로 lib 프로퍼티에는 ES2015(lib.es2015.d.ts 파일) 등의 라이브러리들이 지정되기 때문에 기본적으로 타입 정보를 전역으로 참조할 수 있게 되는 것이다.

lib 프로퍼티를 지정하지 않을 때 자동으로 설정되는 값은 다음과 같다.

- target이 es3이면 디폴트로 lib.d.ts를 사용
- target이 es5이면, 디폴트로 dom, es5, scripthost를 사용
- target이 es6이면, 디폴트로 dom, es6, dom.iterable, scripthost를 사용

<br/>


### **allowJs**
<br/>

TypeScript 프로젝트에서 JavaScript 파일도 컴파일 대상으로 사용할 수 있도록 하는 설정이다. allowJs: true이면 JavaScript 파일들도 타입스크립트 프로젝트에서 import 될 수 있다.

기본적으로 타입스크립트는 .js 확장자를 허용하지 않는다. 그래서 만일 자바스크립트를 타입스크립트로 바꾸는 프로젝트가 진행중이라면 곤란함을 겪게 된다. 따라서 이 속성은 JavaScript 프로젝트를 TypeScript 프로젝트로 바꾸려 할 때 점진적으로 변환하기 위한 용도로 사용된다.

<br/>

### **skipLibCheck**
<br/>


라이브러리 파일의 타입 체킹을 스킵하도록 하는 설정이다. 타입스크립트에 타입 체킹을 안하면 무슨 의미가 있겠냐 싶지만, 만일 프로젝트의 규모가 크면 라이브러리의 선언 파일들이 매우 방대할 텐데, 그것들을 매번 다시 체크하는 것은 상당한 시간이 소모가 된다. 그래서 이 옵션을 true로 지정하여 선언 파일들의 타입 체크를 생략하도록 하여 **컴파일 시간을 줄여주도록** 하기 위한 속성이다.

<br/>

### **strict**
<br/>

타입스크립트의 각종 타입 체킹 동작을 전부 활성화한다.

사실상 이 옵션을 쓰지않는것은 곧 타입스크립트를 쓰지 않는 다는 것과 같다. 따라서 기본으로 활성화 되어 있다.

<br/>

### **forceConsistentCasingInFileNames**
<br/>

파일의 이름을 대소문자 판별하게 하는 옵션이다.

예를 들어, 파일 **`Foo.ts`**와 **`foo.ts`**를 함께 사용하는 것을 방지한다.

프로그래밍 세계에선 같은 알파벳이라도 대소문자를 모두 구분하기 때문에 이 옵션은 가능한 true로 해놓고 사용하기를 권장한다.

<br/>

### **noEmit**
<br/>

타입스크립트를 컴파일하면, JavaScript 변환 파일을 생성하지 않도록 설정한다.

이는 TypeScript 코드를 컴파일하여 JavaScript 파일을 생성하지 않고, 오류만 확인하는 용도로 사용될 수 있다.

<br/>

### **esModuleInterop**
<br/>

CommonJS 모듈과의 상호 운용성을 개선하기 위해 ES 모듈 형식으로 모듈을 가져올 수 있도록 설정

ES6 문법에서는 * 형태로 import 한 것을 함수로 사용할 수 없다. 예를 들어서 다음과 같은 코드는 정상적으로 Javascript로 Transpile 되지만 ES6 문법에 맞지 않는다.

```jsx
// before transpile
import * as moment from 'moment';
moment(); // ES6 문법에 맞지 않음!

// after transpile
const moment = require('moment');
moment();
```

Javascript와의 호환성을 위해 * 형태로 import 해야하는 module들을 default 형태로 import 할 수 있게 해주는 옵션이 esModuleInterop 이다. 아래와 같은 방식으로 동작한다고 생각하시면 된다.

```jsx
// before transpile
import moment from 'moment';
moment(); // ES6 문법에 맞는다!

// after transpile
const moment = __importDefault(require('moment'));
moment.default();
```

위에서 __importDefault 함수가 default가 있는 module은 그대로 두고 없는 module은 default로 바꾸어주는 역할을 한다.

라이브러리 중에서는 amd(웹) 방식을 전제로 구현된 라이브러리가 있는데 commonjs 방식으로 동작하는 TS에서는 혼란을 줄 수 있다. 상호 운용적(interoperable)으로 사용하기 위해서는 가능한 true로 지정해 놓고 타입스크립트 코딩을 하는것을 권한다.

참고 URL 👉 https://velog.io/@bandor/esModuleInterop 

<br/>

### m****odule / moduleResolution****
<br/>


프로그램에서 사용할 모듈 시스템을 결정한다.

모듈 코드를 **`ESNext`** 형식으로 컴파일한다. 이는 최신 모듈 기능을 활용할 수 있게 해준다.

모듈 해결 전략을 **`Node.js`** 스타일로 설정. 이는 모듈을 해석할 때 **`node_modules`** 디렉토리를 탐색하는 방식을 사용한다.

<br/>

### **resolveJsonModule**
<br/>

확장자가 .json인 모듈의 import를 허용하는 설정이다. 생각해 보면 Node.js 자바스크립트 프로젝트에서 json 설정 파일을 import해서 자주 사용해온걸 떠올릴 것이다. 타입스크립트도 가능할 것이라 생각하지만, json의 프로퍼티들을 싹다 타입을 지정해야 사용이 가능하다.

이 옵션은 json의 타입을 자동으로 설정해줘서 따로 변환 작업없이 타입스크립트에서 json 파일 데이터들을 곧바로 사용할 수 있도록 해준다.

<br/>

### isolatedModules
<br/>

일반적으로 TypeScript는 여러 개의 파일로 이루어진 프로젝트를 하나의 컨텍스트에서 컴파일한다. 이는 각 모듈이 전역 네임스페이스를 공유하고, 상호 종속성을 처리하고, 모듈 간의 상호 작용을 가능하게 해준다. 하지만 때로는 파일 간의 분리된 컨텍스트가 필요한 경우가 있을 수 있다.

**`isolatedModules`** 옵션을 **`true`**로 설정하면, TypeScript 컴파일러는 개별 모듈을 독립적인 컨텍스트에서 컴파일한다. 이는 다른 모듈과의 상호 작용을 최소화하고, 파일 간의 종속성을 제한하며, 전역 네임스페이스 오염을 방지할 수 있는 장점을 제공한다.

예를 들어, **`isolatedModules`**를 사용하면 각 파일의 전역 범위에서의 잠재적인 충돌을 방지할 수 있으며, 모듈 간의 인터페이스 정의와 구현을 강제로 분리할 수 있다. 이는 프로젝트의 구조를 더 명확하게 유지하고 오류를 예방하는 데 도움이 될 수 있다.

<br/>

### **jsx**
<br/>

.tsx 확장자의 컴파일 결과 JSX 코드를 어떻게 컴파일할지 결정한다.

- react : .js 파일로 컴파일 된다. (JSX 코드는 React.createElement() 함수의 호출로 변환됨)
- react-jsx : .js 파일로 컴파일 된다. (JSX 코드는 _jsx() 함수의 호출로 변환됨)
- react-jsxdev : .js 파일로 컴파일 된다. (JSX 코드는 _jsx() 함수의 호출로 변환됨)
- preserve : .jsx 파일로 컴파일 된다. (JSX 코드가 그대로 유지됨)
- react-native : .js 파일로 컴파일 된다. (JSX 코드가 그대로 유지됨)

```jsx
"compilerOptions": {
	"jsx": "preserve" // tsx 파일을 jsx로 어떻게 컴파일할 것인지 'preserve', 'react-native', 'react'
}
```
<br/>

### **incremental**
<br/>

이 옵션은 컴파일 시 이전 컴파일 결과를 캐싱하여 증분 컴파일(incremental compilation)을 수행하도록 지시한다.

기본적으로 TypeScript 컴파일러는 전체 프로젝트를 매번 처음부터 다시 컴파일한다. 이는 모든 파일을 다시 처리하고 종속성 그래프를 다시 계산하는 것을 의미한다. 하지만 **`incremental`** 옵션을 **`true`**로 설정하면 컴파일러는 이전 컴파일 결과를 캐싱하여 변경된 파일만 다시 컴파일하고 종속성 그래프를 갱신하기 때문에 컴파일 시간을 대폭 줄이고 개발자의 생산성을 향상시키는 데 도움이 된다.

증분 컴파일을 사용하면 변경 사항이 있는 파일만 다시 컴파일하므로 전체 프로젝트를 다시 컴파일하는 것보다 훨씬 빠르게 개발 및 디버깅할 수 있다. 이는 대규모 프로젝트에서 특히 유용하다.

<br/>

### **baseUrl / paths**
<br/>

**`baseUrl`** 옵션은 상대 모듈 임포트(import) 및 절대 경로 모듈 임포트를 해석하는 기준이 되는 기본 디렉토리 경로를 지정한다. 일반적으로 **`baseUrl`**은 프로젝트의 루트 디렉토리를 가리키도록 설정된다.

**`paths`** 옵션은 모듈 이름을 실제 파일 경로로 매핑하기 위해 사용된다. 이를 통해 긴 상대 경로를 짧은 이름으로 대체할 수 있다. **`paths`**는 이름과 경로 사이의 매핑을 포함하는 객체로 구성된다. 예를 들어:

```jsx
{
  "compilerOptions": {
    "baseUrl": "./src",
    "paths": {
      "@utils/*": ["utils/*"]
    }
  }
}
```

위의 예제에서 **`@utils/*`**는 **`./src/utils/*`**와 같이 해석된다. 이를 통해 **`import "@utils/foo"`**와 같은 형식의 모듈 임포트를 사용하여 해당 모듈을 불러올 수 있다.

**`baseUrl`**과 **`paths`**를 함께 사용하면 모듈 경로를 더 유연하게 구성할 수 있으며, 복잡한 디렉토리 구조에서 모듈을 더 쉽게 찾을 수 있게 된다.