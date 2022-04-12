# DarkMode 제작하기

## Prettier 설정하기

root폴더에 `.prettierrc` 파일을 생성한다.

```javascript
{
    "arrowParens": "always",
    "semi": true,
    "singleQuote": true,
    "useTabs": false,
    "trailingComma": "all",
    "tabWidth": 2,
    "printWidth": 80
}
```

## json파일을 활용하여 import 설정하기

root폴더에 `jsconfig.json`파일을 생성한다

## src폴더 내에 'index.css'에서 폰트 설정 및 여백 설정을 한다.

```javascript
@import url('https://fonts.googleapis.com/css2?family=Jua&display=swap');

body {
  margin: 0;
  font-family: 'Jua', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: inherit;
}
```

## src폴더 내에 'theme.js' 파일을 만든다.

```javascript
export const lightTheme = {
  bgColor: '#fff',
  textColor: '#000',
  headercolor: '#000',
  headerTextColor: '#fff',
};

export const darkTheme = {
  bgColor: '#000',
  textColor: '#fff',
  headercolor: '#fff',
  headerTextColor: '#000',
};
```

## ThemeProvider를 이용하여 테마를 전체 감싸서 다크모드 효과 적용

상단에 import

```javascript
import { ThemeProvider } from 'styled-components';
```

```javascript
return (
  <ThemeProvider theme={toggle ? darkTheme : lightTheme}>
    <DarkMode onToggle={onToggle} toggle={toggle} />
  </ThemeProvider>
);
```

## 스타일 컴포넌트 작성 시 태그 이외의 스타일을 적용 시켜줄 때는 소괄호를 사용

```javascript
const DarkButton = styled(MdDarkMode)`
  cursor: pointer;
  color: ${(props) => props.theme.headerTextColor};
  font-size: 30px;
`;
const LightButton = styled(MdOutlineDarkMode)`
  cursor: pointer;
  color: ${(props) => props.theme.headerTextColor};
  font-size: 30px;
`;
```
