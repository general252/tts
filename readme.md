##### 使用speechSynthesis文字转语音

```
var utterThis = new SpeechSynthesisUtterance();

utterThis.onstart = function (event) {
	console.log("onstart", event);
}
utterThis.onerror = function (event) {
	console.log("onerror", event);
}
utterThis.onend = (event) => {
	console.log("onend", event);
}

utterThis.text = "你好";
utterThis.lang = "zh-cn";
utterThis.volume = 1; //  [0, 1]
utterThis.rate = 1.0; // 语速 [0.1, 10]
utterThis.pitch = 1; // 音高 [0, 2]

var voices = speechSynthesis.getVoices();
for (i = 0; i < voices.length; i++) {
	if (voices[i].name === "Microsoft Yaoyao - Chinese (Simplified, PRC)") {
		// 设置语音
		utterThis.voice = voices[i];
		break;
	}
}

// 播放语音
speechSynthesis.speak(utterThis);

setTimeout(() => {
	// 停止语音播放
	speechSynthesis.cancel();
}, 10000);
```

