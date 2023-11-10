TypeScript 是一种向 JavaScript 代码添加类型定义的常用方法。TypeScript 天然支持 JSX

https://www.runoob.com/w3cnote/getting-started-with-typescript.html

## 类型批注
基本类型的批注是number, bool和string。而弱或动态类型的结构则是any类型。

1. 使用 `interface` 或 `type` 来描述组件的 props类型 (react)
```js
interface MyButtonProps {
  /** 按钮文字 */
  title: string;
  /** 按钮是否禁用 */
  disabled: boolean;
}

function MyButton({ title, disabled }: MyButtonProps) {
  return (
    <button disabled={disabled}>{title}</button>
  );
}
```