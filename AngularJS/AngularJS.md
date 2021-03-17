# AngularJS

# 모듈

관련된 기능을 하나로 묶어 다른 코드와 결합도를 줄이고 재사용성을 높이기 위해 사용

### 모듈선언

```jsx
angular.module("모듈이름", ["사용할 모듈", ...])
```

- angular.module 함수를 사용해 모듈을 만들면 모듈 인스턴스가 반환되는데 해당 모듈 인스턴스는 컨트롤러, 서비스, 지시자, 필터들을 담는다.

### 모듈 인스턴스가 사용할 수 있는 메서드

- Module.config(configFuntion) - 모듈이 로딩될 때 호출되며 config 함수에 해당 익명 함수로 서비스를 설정할 수 있다.
- Module.constant(name, object) - 모듈에서 사용되는 상수를 등록한다.
- Module.controller(name, constructor) - 모듈에서 사용되는 컨트롤러를 등록한다.
- Module.directive(name, directiveFactory) - 모듈에서 사용되는 지시자를 등록한다.
- Module.factory(name, providerFunction) - 모듈에서 사용되는 서비스를 팩토리형태로 등록한다.
- Module.filter(name, filterFactory) - 필터를 등록한다.
- Module.provider(name, providerType) - 서비스를 제공하는 프로바이더를 등록한다.
- Module.run(initializationFn) - 앱 초기화 함수를 등록한다. 모든 모듈의 등록을 완료했을때 초기화 함수가 실행된다.
- Module.service(name, constructor) - 서비스를 등록한다.
- Module.value(name, object) - 객체를 등록한다.

### AJS에서 모듈의 의미

컨트롤러, 서비스,  필터, 지시자를 담는 그릇

- 하나의 웹 앱은 하나의 모듈을 지정할 수 있다.
- 해당 모듈은 자바의 메인메서드와 같은 역할을 하는 run함수를 이용해 앱 시작에 대한 로직을 작성 가능
- 그리고 해당 앱에서 사용하는 컨트롤러, 서비스, 필터 그리고 지시자를 등록할 수 있다.

# 기본 개념

1. Scope
    - Scope는 모델 변경을 감지하고 표현하기위한 책임을 갖는다.
    - Scope는 DOM 구조와 가깝게 하이어라키 구조를 갖는다.
2. Model
    - 모델은 화면 템플릿에 합쳐지는 데이터를 가지고 있는 일반 자바스크립트 객체. (데이터라고 생각하면 된다.)
    - Scope는 항상 모델을 참조하고 있다.
3. View
    - 템플릿 스트링과 모델을 합쳐서 HTML을 만들고 DOM으로 해석되어 Browser에 표현된다.
    - Angular는 템플릿이 HTML이어서 바로 DOM으로 해석되고 DOM 안에 directive가 템플릿 엔진인 $compile지시어를 통해 $watch를 설정하고 모델의 변경을 계속 감시하게 된다.
    - View는 템플릿으로 Scope의 투영체이고, Scope는 Model과 View의 연결하며 controller로 이벤트를 보내는  역할을 한다.
4. Controller
    - Controller는 View 뒤에서 반드시 수행하는 코드이다.
    - Controller 역할은 모델을 생성하고 콜백 메소드를 가지고 View로 퍼블리싱을  담당한다.
    - Controller는 자바스크립트이고 업무적 행위를 정의한다. 또한 DOM rendering 정보가 일체 없다.
5. Directives (지시어)
    - 지시어는 HTML을 확장하여 주고 행위를 일으키는 주체
    - 예를 들어  앞의 예제에서 보았듯이  데이터 바인딩을 위한 이중 중괄호 표기{{}}, 컨트롤러가 뷰의 어느부분을 감독할지를 지정하는 ng-controller, 인풋을 해당 모델의 구성물에 바인딩하는 ng-model모두 directive를 이용한 확장 문법이다.

# 디렉티브

쉽게말해 AngularJS의 HTML Compiler에 의해 해석된 특정한 행위의 기능을 가진 DOM 엘리먼트

built-in 된, 또는 사용자가 새롭게 생성한 사용자정의 디렉티브를 HTML에서 사용할 수 있는 이유는 AngularJS의 HTML Compiler가 HTML의 DOM을 돌면서 디렉티브 이름과 같은 DOM 엘리먼트를 찾아내기 때문이다. AngularJS의 Compiler의 절차는 다음 2단계로 축약할 수 있다.

- compile 단계 : HTML의 DOM 엘리먼트들을 돌면서 디렉티브를 찾는다.

    (attribute name, tag name, comments, class name을 이용해 디렉티브를 매칭시킨다.)

    결과로 link function을 리턴한다.

- link 단계 : 디렉티브와 HTML이 상호작용(동적인 view) 할 수 있도록 디렉티브에 event listener를 등록하며 scope와 DOM 엘리먼트간에 2-way data binding을 위한 $watch를 설정한다.

    위의  HTML Compiler의 두 단계를 거쳐 HTML에서 디렉티브를 사용할 수 있게 된다.

## 작명법

- Javascript에서 AngularJS의 디렉티브 생성시 디렉티브 이름은 camelCase 작명법을 따라 작성

    (ex : testDirective)

- HTML에서 AngularJS의 디렉티브를 사용시 '-'를 이용한 snake-case 작명법으로 사용

    (ex : test-directive)

```html
<my-example></my-example>
<my:example></my:example>
<my_example></my_example>
```

```jsx
angular.module.(...)
	.directive('myExample', function() {
	)};
```

위처럼 HTML에서는 snake-case 작명법이 아닌 ':', '_' 등 여러가지 방법으로 디렉티브를 사용할 수 있으며 모두 동일한 결과를 나타낸다. 하지만 snake-case를 이용한 사용법을 선호한다.

## 디렉티브 생성방법

```jsx
var myModule = angular.module(...);
myModule.directive('directiveName', function(injectables) {
	return {
		restrict: 'A',
		template: '<div></div>',
		templateUrl: 'directive.html',
		replace: false,
		priority: 0,
		transclude: false,
		scope: false,
		terminal: false,
		require: false,
		controller: function($scope, $element, $attrs, $transclude, otherInjectables) {...},
		compile: function compile(tElement, tAttrs, transclude) {
			return {
				pre: function preLink(scope, iElement, iAttrs, controller) {...},
				post: function postLink(scope, iElement, iAttrs, controller) {...}
			}
		link: function postlink(scope, iElement, iAttrs) {...}
	};
});
```

### restrict

HTML에서 디렉티브를 사용하기 위한 DOM 엘리먼트의 속성을 설정

restrict 규칙을 생략할 경우는 'A'로 선언한 것과 같은 효과를 나타내며 종류는 다음과 같다.

![AngularJS%206fecbda5fbd44f0692f3d4b1dcc2e55c/Untitled.png](AngularJS%206fecbda5fbd44f0692f3d4b1dcc2e55c/Untitled.png)

```html
<!doctype html>
<html ng-app="exampleDirective">
	<head>
		<script src="http://code.angularjs.org/1.2.10/angular.min.js"></script>
		<script src="script.js"></script>
	</head>
	<body>
		<div ng-controller="Ctrl">
			<my-example></my-example>
		</div>
	</body>
</html>
```

```jsx
angular.module('exampleDirective', [])
	.controller('Ctrl', function($scope) {
		$scope.person = {
			name: 'nextreeMember',
			address: 'Gasan'
		};
	})
	.directive('myExample', function() {
		return {
			restrict: 'E',
			template: 'Name: {{person.name}} </br> Address: {{person.address}}'
		};
});
```

### template

html의 디렉티브를 사용한 부분에 보여줄 내용으로 In-Line value를 설정

```html
<!doctype html>
<html ng-app="exampleDirective">
	<head>
		<script src="http://code.angularjs.org/1.2.10/angular.min.js"></script>
		<script src="script.js"></script>
	</head>
	<body>
		<div ng-controller="Ctrl">
			<my-example></my-example>
		</div>
	</body>
</html>
```

```jsx
angular.module('exampleDirective', [])
	.controller('Ctrl', function($scope) {
		$scope.person = {
			name: 'nextreeMember',
			address: 'Gasan'
		};
	})
	.directive('myExample', function() {
		return {
			restrict: 'E',
			template: 'Name: {{person.name}} </br> Address: {{person.address}}'
		};
});
```

```markdown
<결과>
Name : nextreeMember
Adress : Gasan
```

위의 예제에서 보면 myExmple디렉티브는  In-Line value인 template를 리턴하고 있다. template의 내용이 많아지면 많아질수록 소스코드를 어지럽히기 때문에 template의 내용이 매우작지않은이상 templateUrl option을 이용하여 template를 HTML파일로 분리시키는것을 지향한다.

### templateUrl

template을 별도의 html 파일로 관리

templateUrl에 선언한  url에 해당하는 HTML을 로드한다. 이때 index.html 위치를 기준으로 로드할 html의 상대위치를 정의한다.

```html
<!doctype html>
<html ng-app="exampleDirective">
	<head>
		<script src="http://code.angularjs.org/1.2.10/angular.min.js"></script>
		<script src="script.js"></script>
	</head>
	<body>
		<div ng-controller="Ctrl">
			<my-example></my-example>
		</div>
	</body>
</html>
```

```jsx
angular.module('exampleDirective', [])
	.controller('Ctrl', function($scope) {
		$scope.person = {
			name: 'nextreeMember',
			address: 'Gasan'
		};
	})
	.directive('myExample', function() {
		return {
			templateUrl: 'my-example.html'
		};
});
```

```html
<!-- my-example.html -->
Name: {{person.name}} </br> Address: {{person.address}}
```

### replace

디렉티브를 사용한 HTML의 태그에 template 또는 templateUrl에 포함된 태그 내용을 추가할지 교체할지 설정

true로 설정할 경우 HTML의 디렉티브를 사용한 태그를 template또는 templateUrl에 작성된 내용으로 교체한다.

```html
<!doctype html>
<html ng-app="exampleDirective">
	<head>
		<script src="http://code.angularjs.org/1.2.10/angular.min.js"></script>
		<script src="script.js"></script>
	</head>
	<body>
		<div ng-controller="Ctrl">
			<my-example></my-example>
		</div>
	</body>
</html>
```

```jsx
angular.module('exampleDirective', [])
	.controller('Ctrl', function($scope) {
		$scope.person = {
			name: 'nextreeMember',
			address: 'Gasan'
		};
	})
	.directive('myExample', function() {
		return {
			restrict: 'E',
			template: '<div>Hello AngularJS</div>',
			replace: true
		};
});
```

### priority

디렉티브 별로 compile()과 link()의 호출우선순위를  지정. (기본값은  0)

priority 값이 클수록 우선순위가 높고 먼저 호출됨

### transclude

ng-transclude를 이용하여 template 또는 templateUrl에서 디렉티브내의 원본내용을 포함시킬지 설정

true로 설정시 디렉티브에 포함된 원본내용을 template의 ng-transclude를 사용한 곳으로 포함한다.

```html
<!doctype html>
<html ng-app="exampleDirective">
	<head>
		<script src="http://code.angularjs.org/1.2.10/angular.min.js"></script>
		<script src="script.js"></script>
	</head>
	<body>
		<div ng-controller="Ctrl">
			<my-example>Hello AngularJS</my-example>
		</div>
	</body>
</html>
```

```jsx
angular.module('exampleDirective', [])
	.controller('Ctrl', function($scope) {
		$scope.person = {
			name: 'nextreeMember',
			address: 'Gasan'
		};
	})
	.directive('myExample', function() {
		return {
			restrict: 'E',
			template: '<div>Name: {{person.name}} </br> Address: {{person.address}} </br> <span ng-transclude></div>', 
			transclude: true
		};
});
```

```markdown
<결과>
Name: nextreeMember
Adress: Gasan
Hello AngularJS
```

### scope

디렉티브의 scope를 설정

- scope: false → 새로운 scope 객체를 생성하지 않고 부모가 가진 같은 scope객체를 공유. (default 옵션)
- scope: true → 새로운 scope 객체를 생성하고 부모 scope 객체를 상속
- scope: {...} → isolate/isolated scope를 새롭게 생성

scope: {...}는 재사용 가능한 컴포넌트를 만들때 사용하는데 컴포넌트가 parent sscope의 값을 read/write 못하게 하기 위함이다. parent scope에 접근하고싶을경우 Binding 전략(=, @, &)를 이용

Binding 전략

- = : 부모 scope의 property와 디렉티브의 property를 data binding하여 부모 scope에 접근
- @ : 디렉티브의 attribute value를 {{}}방식(interpolation)을 이용해 부모 scope에 접근

['='를 이용한 예]

```html
<div ng-controller="Ctrl">
	<nextree-directive company-info="nextree"></nextree-directive>
</div>
```

```jsx
angular.module('testDirective', [])
	.controller('Ctrl', function($scope) {
		$scope.nextree = {name: 'Nextree'};
	})
	.directive('nextreeDirective', function() {
		return {
			restrict: 'E',
			scope: {
				myCompany: '=companyInfo'
			},
			template: 'Name: {{myCompany.name}}'
	};
});
```

[@를 이용한 예]

```html
<div ng-controller="Ctrl">
	<nextree-directive company-info={{name}}>
	{{locate}}
	</nextree-directive>
</div>
angular.module('testDirective', [])
	.controller('Ctrl', function($scope) {
		$scope.name = 'Nextree';
		$scope.locate = 'Gasan';
	})
	.directive('nextreedirective', function() {
		return {
			restrict: 'E',
			scope: {
				name: '@companyInfo'
			}
		};
});
```

@방식은 scope의 내용을 string으로 치환한것과 같은 효과를 가진다. (company-info='Nextree')

### controller()

다른 디렉티브들과 통신하기 위한 역할을 하는 controller 명칭을 정의

controller() 내부에서는 $scope와 this를 사용하여 data 및 function 을 정의한다.

this로 정의된 data 및 function은 require rule을 사용하여 다른 디렉티브에서 액세스 할 수  있게 한다.

### require

AngularJS의 다른 컨트롤러나 디렉티브 controller()에 this로 정의된 function을 사용할 때 선언

require에 컨트롤러 이름을 설정하면 해당 컨트롤러를 주입받게 된다. 이후 디렉티브의 link() 내에서 주입받은 컨트롤러의 this로 선언된 모든 function을 사용할 수 있다.

require 추가 옵션

- ?를 디렉티브이름앞에 추가 시 매칭되는 디렉티브가 없어도 에러가 발생안함
- ^를 추가시 DOM 엘리먼트들을 거슬러 올라가면서 해당 디렉티브를 찾음

### compile()

DOM 엘리먼트를 해석하여  디렉티브로 변환하며 두 종류의 link function 을 리턴

리턴되는 link function 종류

- preLink() : compile phase가 실행되고 child 엘리먼트가 link 되기전에 호출
- postLink() : compile phase가 실행되고 child 엘리먼트가 link 된 후 호출(따라서, DOM 구조를 변경하기 위해서 postLink()를 이용)

### link()

2-way data binding을 위해 해당 디렉티브 DOM 엘리먼트의 event listener를 등록. (디렉티브의 대부분의 로직을 여기에 선언하며 postLink()만 지원)

# 필터

값의 표시를 조작 가능

형식 : {{변수 | 필터}}

     여러 필터를 동시에 사용하려면 {{변수 | 필터1 | 필터2 | ...}}

- PRICE 출력

```html
{{obj.price | currency : '\'}}
```

숫자를 금액으로 포맷하여 표시하는 필터. 출력된 표시를 보면 "\ 7,800.00"라는 형식으로 표시된다.

- DATE 출력

```html
{{obj.date | date : 'yyyy-MM-dd'}}
```

Date객체의 값을 특정 형식으로 포맷하는 필터. "2015-12-14"라는 형식으로 날짜가 표시된다.

## 표준필터

AngularJS에 표준으로 제공되는 필터

- currency - 숫자를 금액으로 표기하기 위한 필터. 단순히 currency만 지정하면 달러표기로 표시
- date - Date 값을 정해진 형식의 날짜 텍스트에 서식하는 필터. 포맷의 이름이나 어떤 패턴을 값으로 지정
- number - 숫자를 특정 자릿수로 반올림하여 표시하는 필터. 예를들어 number : 4라고 하면 앞에 4자리만 표시하고 5번째 자리를 반올림한다.
- json - 객체의 값을 JSON 형식으로 변환하여 출력하는 필터
- uppercase / lowercas - 텍스트를 모두 대문자 또는 소문자로 변환하는 필터

## 커스텀 필터

필터는 기본적으로 제공되는 것 뿐만 아니라 사용자가 직접 필터를 만들 수 있다. 이 커스텀 필터는 다음과 같은 형태로 정의된다.

```html
컨트롤러.filter(이름, 함수);
```

인수에 설정되는 함수는 대체로 다음과 같은 형태로 정의해야 한다.

```jsx
function(val) {
	...
	return 값;
}
```

인수로 전달되는것이 필터에 걸린 원래 값이다. 그리고 return 하는 것이 필터링된 값이다. 즉, 함수에서 인수값을 어떻게 변환하여 return 할지 생각하면서 코딩하면 필터는 비교적 쉽게 만들 수 있다.

ex) boolean 값에 따라 알기쉽게 표시하는 필터

```jsx
helo.filter('getIt', 
	function() {
		return function(val) {
			return val ? "✔" : "-";
		};
	}
};
```

```jsx
<td>{{obj.get | getIt}}</td>
```

### 필터에 값을 설정

필터에는 currency 나 date 처럼 어떤 값을 설정하고 호출할 수 있다. 필터함수를 정의할 때 두번째 인수를 지정하여 값을 전달 

```jsx
helo.filter('getIt',
	function() {
		return function(val, opt) {
			var t = (opt == null) ? '✔' : opt;
			return val ? t : '-';
		};
	}
};
```

```jsx
<td>{{obj.get | getIt:'●'}}</td>
```

++tip

- 코드 작성시 주석으로 구분해서 작성하는것이 좋다.

```jsx
/***************************************
* $scope resource
**************************************/
...
/***************************************
* $scope funtion
**************************************/
...
/***************************************
* funtion
**************************************/
...
/***************************************
* init
**************************************/

```

- 함수는 재사용 할 수 있게 통신에 필요한 최소한의 부분만 들어가는것이 좋다.

    나머지 로직은 함수를 부르는 $scope안에서 구현하는것이 좋다.

```jsx
$scope.modify = function() {
	
};

function modify() {
	$http()
};
```