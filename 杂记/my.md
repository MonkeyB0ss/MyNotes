# RN键盘将底部导航栏顶上去预解决方案

```javascript
import { View, KeyboardAvoidingView } from "react-native";

// ....

<KeyboardAvoidingView behavior="padding" style={{ flex: 1 }}>
  {/* 这里放置你的底部导航组件 */}
</KeyboardAvoidingView>;
```

```javascript
import { View, Keyboard, Platform } from 'react-native';

// 在组件的构造函数或 useEffect 中添加事件监听
componentDidMount() {
  this.keyboardDidShowListener = Keyboard.addListener(
      Platform.OS === 'ios' ? 'keyboardWillShow' : 'keyboardDidShow',
    this.keyboardDidShow
  );
  this.keyboardDidHideListener = Keyboard.addListener(
    Platform.OS === 'ios' ? 'keyboardWillHide' : 'keyboardDidHide',
    this.keyboardDidHide
  );
}

// 在组件卸载时移除事件监听
componentWillUnmount() {
  this.keyboardDidShowListener.remove();
  this.keyboardDidHideListener.remove();
}

// 处理键盘弹出事件
keyboardDidShow = () => {
  // 在键盘弹出时，调整底部导航的样式
  // 可以通过设置底部导航的 marginBottom 来使其上移
  // this.setState({ bottomNavigationMargin: ... });
}

// 处理键盘隐藏事件
keyboardDidHide = () => {
  // 在键盘隐藏时，还原底部导航的样式
  // this.setState({ bottomNavigationMargin: 0 });
}
```
