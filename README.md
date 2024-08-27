# Tailwind css



### Set-up

- 시작하기
  
  - npm install -D tailwindcss postcss autoprefixer
  
  - npx tailwindcss init -p
  
  - tailwind.config.ts(js) 안의 content에
    `'./pages/**/*.{ts,tsx}',`
    
    `'./components/**/*.{ts,tsx}',`
    
    `'./app/**/*.{ts,tsx}',`
    
    `'./src/**/*.{ts,tsx}',`
    
    추가, 기본적으로 next랑 react 생성시에는 tailwind 포함해서 설치하면 만들어져있음.

- VS Code Extension : Tailwind css Intellisense 자동완성

- Reponsive Design
  
  - Screen
    
    - sm : 640px @media (min-width: 640px) {}
    
    - md : 768px @media (min-width: 768px) {}
    
    - lg : 1024px @media (min-width: 1024px) {}
    
    - xl : 1280px @media (min-width: 1280px) {}
    
    - 2xl : 1536px @media (min-width: 1536px) {}
  
  - State
    
    - Hover, Focus
    
    - First,last, odd and even
    
    - Before, After
    
    - placeholder
    
    - marker
    
    - selection
    
    - 사용하기  : `{State}:{style}` ex) `hover:bg-sky-700`



### Colors

- 사용하기 : `{위치}-{색}(-진한정도)` ex) `text-green-500`

- 위치 종류 : text(글자), bg(배경), border(테두리) 등

- Custom 하는 법
  
  1. tailwind.config.ts 안에서 수정
  
  2. theme: 안에 colors 안에 색의 이름을 정의해서 사용
  
  3. 정의하게되면 overwriting을 한 것이여서 정의한것만 사용가능
  
  4. extend를 사용해서 하면 추가를 해서 사용가능하니 전부 커스텀하지 않을 거면 extend해서 사용하는 것이 나음.



### Customization

- screens : 자기만의 스크린 재설정 가능

- spacing : 자기만의 공간 재설정 가능

- Custom 하는 법
  
  1. tailwind.config.ts 안에서 수정
  
  2. theme: 안에 바꿀 값을 정의해서 사용
  
  3. 정의하게되면 overwriting을 한 것이여서 정의한것만 사용가능

- Value 바로 쓰는법
  
  - 새로 정의하는 것이 여러 곳에서 쓰이지 않고 확장성이 필요 없다면 바로 재정의
  
  - 사용법 `{state}-[재정의]` ex) `top-[110px]`
  
  - 색도 정의 가능 ex) `bg-[#bada55]` 

- layer
  
  - base : 기본 스타일을 위한 레이어
  
  - components : 클래스 기반 스타일을 위한 레이어
  
  - utilities : 소규모 단일 목적 클래스를 위한 레이어
  
  - utillities > components > base 순으로 css 적용 utillities가 우선순위 1등
    
    ```typescript
    @layer base {
        html {
            @apply bg-slate-500
        }
    }
    ```



### Typography

- fontSize도 마찬가지로 기본적으로 정의된거 말고 Custom해서 사용가능
  
  - ```typescript
    theme: {
        fontSize: {
            sm: '0.8rem',
            base: '1rem',
            xl: '1.25rem',
            2xl: '1.563rem',
            3xl: '1.985rem',
            4xl: '2.44rem',
        }
    }
    ```

- Font Family

```typescript
@import url('https://fonts.googleapis.com/css2?family=Noto+Serif+KR:wght@200..900&display=swap');

.noto-serif-kr-<uniquifier> {
  font-family: "Noto Serif KR", serif;
  font-optical-sizing: auto;
  font-weight: <weight>;
  font-style: normal;
}
```

- Font Style
  
  - italic(기울여서), normal

- Text Decoration
  
  - underline 밑줄
  
  - line-through 가운데줄
  
  - overline 윗줄
  
  - Text Decoration Color
    
    - text-decoration-color
  
  - Text Decoration Style
    
    - decoration-solid(실선), double(실선2개), dotted(점선), dashed(대쉬선), wavy(물결)
  
  - Text Decoration Thickness
    
    - decoration-{value} : 굵기 조정
  
  - Text Underline Offset
    
    - underline-offset-{value} : offset(사이 공간)

- Line Height
  
  - leading-{value} : 줄간격

- Text Transform
  
  - uppercase : 전부 대문자
  
  - lowercase : 전부 소문자
  
  - capitalize : 첫 단어만 대문자
  
  - normal-case : 평범

- Text Overflow
  
  - Truncate : 긴문장이 width를 벗어날 경우 ...으로 변경
  
  - whitespace-nowrap : 자동으로 줄바꿈이 일어나지 않게

- Word Break
  
  - Normal :
  
  - break-words : 한 단어가 길어도 부숨
  
  - break-all : 띄어쓰기 필요없이 그냥 width 에 맞춰서 글자를 보여줌.



### Spaces & Sizes

- Padding : 안쪽 Area, bg의 영향받음.
  
  - p-{value} : 4방위
  
  - px, py : x축, y축
  
  - pt, pb, pl, pr : 위, 아래, 왼, 오

- Margin : 바깥쪽 Area, bg 영향 받지 않음.
  
  - m-{value} : 4방위
  
  - mx, my : x축, y축
  
  - mt, mb, ml, mr : 위, 아래, 왼, 오
  
  - negative value 사용가능
    
    - ex) `-mt-8` : 위쪽으로 이동함.

- Width, Height
  
  - w or h - {value} : 고정값
  
  - w-1/2 : witdh 50%, 부모 width 값에 따른 비율

- Min-Witdh(Height)
  
  - min-w-{value} 최소길이지정

- Max-Width(Height)
  
  - max-w-{value} 최대길이지정

- space-{axis}-{value}
  
  - space-x-2 : x축의 공간 띄움



### Flex

- 한 축(행 또는 열)을 기반으로 요소를 정렬하고 배치하기 위한 레이아웃

- 주로 단일 차원(행 또는 열)에서 유연한 레이아웃을 구현하는 데 사용

- ex) 내비게이션 바 or 작은 아이템 목록 정렬



### Grid

- 행과 열의 2차원 그리드를 사용하여 복잡한 레이아웃을 만들기 위한 레이아웃

- Flex와 달리 2차원 레이아웃을 제공하여 더 복잡하고 다양한 디자인 구현 가능

- 명확하게 지정하고 배치하는 데 중점을 둔 복잡한 구조

```tsx
 // 2열 배치
 <div className="grid grid-cols-2 gap-2">
     <div className="p-6 rounded-lg bg-sky-500">element</div>
     <div className="p-6 rounded-lg bg-sky-500">element</div>
 </div>
```

- grid 내에서 크기가 더 큰 것을 만들려면 col-span-{value} 사용
  
  ```tsx
   <div className="grid grid-cols-4 gap-2">
       <div className="p-6 rounded-lg bg-sky-500">element</div>
       <div className="p-6 rounded-lg bg-sky-500">element</div>
       <div className="col-span-2 p-6 rounded-lg bg-sky-500">element</div>
       <div className="p-6 rounded-lg bg-sky-500">element</div>
       <div className="p-6 rounded-lg bg-sky-500">element</div>
       <div className="p-6 rounded-lg bg-sky-500">element</div>
   </div>
  ```
  
  - 상위 cols의 수보다 큰 span 수를 사용할 경우 제대로 작동하지 않음.

- col-start, end, span
  
  ```tsx
   <div className="grid grid-cols-6 gap-2">
       <div className="col-span-4 col-start-2 p-6 rounded-lg bg-sky-500">element</div>
       <div className="col-start-1 col-end-3 p-6 rounded-lg bg-sky-500">element</div>
       <div className="col-span-2 col-end-7 p-6 rounded-lg bg-sky-500">element</div>
       <div className="col-start-1 col-end-7 p-6 rounded-lg bg-sky-500">element</div>
   </div>
  ```

- row도 똑같이 쓸 수 있으며, 순서가 위에서 아래로 변경되고 벗어날 경우 오른쪽으로 이동해서 col이 추가되는 형식

- grid-flow-row-dense : grid-cols-3에서 col-span-2 col-span-2 col-span-1 이 나올 경우 순서대로 나오지 않고 뒤에서 앞으로 칸을 넣을 수 있는 것이 넘어옴

![](C:\Users\ssginc56\AppData\Roaming\marktext\images\2024-08-26-15-37-12-image.png)



### Layouts

- Container
  
  - columns-{value} : 몇 개의 column으로 보일지 설정

- Display
  
  - 
