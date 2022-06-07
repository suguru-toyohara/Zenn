---
title: "TypeScript＋Reactの感覚を掴む #ts勉強ログ002"
emoji: "🍰"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["TypeScript"]
published: false
---

# まず試すもの。

https://qiita.com/yonetty/items/012be4c5c6258a609e35

こちらをローカルで試してみる。

```typescript:index.tsx
import ReactDOM from "react-dom";
import App from "./App";

ReactDOM.render(<App />, document.querySelector(".container"));

```

```typescript:App.tsx

import AdmissionFeeCalculator from "./components/Calc";
import React from "react";
import "./App.css";
const App: React.FC = () => {
	return (
		<div className="main">
			<AdmissionFeeCalculator />
		</div>
	);
};

export default App;

```

```typescript:Calc.tsx
import React from 'react';
import Detail from './Detail';
import Summary from './Summary';

class AdmissionFeeCalculator extends React.Component {
  render() {
    return (
      <>
        <Detail />
        <Summary />
      </>
    );
  }
}

export default AdmissionFeeCalculator;

```

```typescript:Detail.tsx
import React from 'react';

class Detail extends React.Component {
  render() {
    return (
      <div>
        <div className="classification-name">名前</div>
        <div className="description">説明</div>
        <div className="unit-price">0円</div>
        <div className="num-people">
          <select value="0">
            <option value="0">0</option>
            <option value="1">1</option>
            <option value="2">2</option>
            <option value="3">3</option>
            <option value="4">4</option>
          </select>
          <span>名</span>
        </div>
      </div>
    );
  }
}

export default Detail;

```

```typescript:Summary.tsx
import React from 'react';

class Summary extends React.Component {
  render() {
    return (
      <div>
        <div className="party">
          <input type="text" className="party" value="0" />
          <span>名様</span>
        </div>
        <div className="total-amount">
          <span>合計</span>
          <input type="text" className="total-amount" value="0" />
          <span>円</span>
        </div>
      </div>
    );
  }
}

export default Summary;

```

これをもとに記事通り要素を追加していく。

