## एक ग्रिड बनाएँ

आप ठप्पा वाले परिधानों का एक ग्रिड बनाने जा रहे हैं:

![ग्रिड में मोहरें](images/stamp_grid.png)

ऐसा करने के लिए आपको `x`{:class="block3motion"} और `y`{:class="block3motion"} निर्देशांकों को जानने की ज़रूरत होगी जहाँ प्रत्येक ठप्पा लगाई जानी चाहिए।

--- task ---

सबसे पहले, एक नया ब्लॉक बनाएं जिसे `generate positions`{:class="block3myblocks"} कहा जाए। ब्लॉक में दो 'नंबर इनपुट' पैरामीटर होना आवश्यक है। इन दो पैरामीटरों का नाम `rows`{:class="block3myblocks"} और `columns`{:class="block3myblocks"} रखें।

इन पैरामीटरों के मान यह तय करेंगे कि आपके ग्रिड में कितनी पंक्तियाँ और कॉलम हैं।

[[[generic-scratch3-make-block]]]

```blocks3
define generate positions (rows)(columns)
```

--- /task ---

--- task ---

दो सूचियाँ बनाएँ, और उनमें से एक को `x_positions`{:class="block3variables"}और दूसरी को `y_positions`{:class="block3variables"} नाम दें। ये सूचियाँ ठप्पा के लिए `x`{:class="block3motion"} और `y`{:class="block3motion"} निर्देशांकों को संग्रहण करने के लिए हैं।

--- /task ---

--- task ---

अपने `generate positions`{:class="block3myblocks"} ब्लॉक के अंदर, दोनों सूचियों में से सभी मदों को हटाने के लिए ब्लॉक जोड़ें, ताकि हर बार जब गेम शुरू हो, तो सूचियाँ खाली हों।

```blocks3
define generate positions (rows)(columns)
+ delete [all v] of [y_positions v]
+ delete [all v] of [x_positions v]
```

--- /task ---

--- task ---

इसके बाद, दो वेरिएबल बनाएँ, और उनमें से एक को `x_pos`{:class="block3variables"} नाम दें और दूसरे को `y_pos`{:class="block3variables"}।

--- /task ---

इस `x_positions`{:class="block3variables"} सूची में कुल मिलाकर दस संख्याएँ होनी चाहिए, और ये `-200`{:class="block3variables"} से शुरू होनी चाहिए और `200`{:class="block3variables"} तक जानी चाहिए।

अभी के लिए, `y_positions`{:class="block3variables"} सूची में संख्या `-150`{:class="block3variables"} केवल दस बार शामिल हो सकती है, ताकि ग्रिड में केवल एक पंक्ति हो।

--- task ---

से कोड जोड़कर प्रारंभ करें `generate positions`{:class="block3myblocks"}ब्लॉक सेट करने के लिए `y_pos`{:class="block3variables"}बदलने वाला`-150`{:class="block3variables"}और यह `x_pos`{:class="block3variables"}बदलने वाला`-200`{:class="block3variables"} यह ठप्पा वाले पहले स्प्राइट का स्थान है।

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
+ set [y_pos v] to [-150]
+ set [x_pos v] to [-200]
```

--- /task ---

--- task ---

उसके बाद, निर्देशांकों को सूचियों में जोड़ने के लिए एक `repeat`{:class="block3control"} लूप जोड़ें।

`repeat`{:class="block3control"} लूप को हर उस क़तार के लिए एक बार चलना चाहिए जिसे आप ग्रिड में रखना चाहते हैं।

`generate positions`{:class="block3myblocks"} ब्लॉक `columns`{:class="block3myblocks"} को इनपुट के रूप में लेता है, इसलिए आप `columns`{:class="block3myblocks"} का उपयोग `repeat`{:class="block3control"} लूप के लिए कर सकते हैं।

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
+ repeat (columns :: custom-arg)
```

--- /task ---

`repeat`{:class="block3control"} लूप के भीतर, सूचियों में `x_pos`{:class="block3variables"} और `y_pos`{:class="block3variables"} के मान जोड़ें। फिर आपको `x_pos`{:class="block3variables"} का मान थोड़ा सा बढ़ाने की ज़रूरत होगी। `x_pos`{:class="block3variables"} का मान कितना बढ़ना चाहिए?

इसका पता इस तरह लगाया जा सकता है:

- `x_pos`{:class="block3variables"} `-200`{:class="block3variables"} के मान से प्रारंभ होता है
- लूप `repeat`{:class="block3control"} जब अंतिम बार चलता है तो, `x_pos`{:class="block3variables"} को `200`{:class="block3variables"} के मान पर पहुँचना चाहिए
- यह कुल `400`{:class="block3variables"} की वृद्धि है
- पहला `x_pos`{:class="block3variables"} मान ग्रिड पर पहले कॉलम के लिए है, और कुल कितने कॉलम हैं यह `columns`{:class="block3myblocks"} की इनपुट से निर्धारित होता है।

इसलिए पहले `x_pos`{:class="block3variables"} मान को जोड़ लेने के बाद, लूप के इर्द-गिर्द, `x_pos`{:class="block3variables"} के मान में हर बार `400 / (columns - 1)`{:class="block3operators"} की वृद्धि होनी चाहिए

--- task ---

इसमें कोड जोड़ें जो `x_pos`{:class="block3variables"} और `y_pos`{:class="block3variables"} के सभी मानों को `x_positions`{:class="block3variables"} और `y_positions`{:class="block3variables"} सूचियों में जोड़ेगा।

--- hints ---
 --- hint ---

लूप के भीतर, आपको `x_pos`{:class="block3variables"} को `x_positions`{:class="block3variables"} सूची में जोड़ना होगा, और `y_pos`{:class="block3variables"} को `y_positions`{:class="block3variables"} सूची में जोड़ना होगा। फिर `x_pos`{:class="block3variables"} वोरिएबल को लूप के हर बार दोहराए जाने पर `400 / (columns -1)`{:class="block3operators"} से बढ़ना चाहिए।

--- /hint --- --- hint ---

यह उन अतिरिक्त ब्लॉकों को दर्शाता है जिन्हें आपको अपनी स्क्रिप्ट में जोड़ने की ज़रूरत होगी।

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
repeat (columns :: custom-arg)
end

(x_pos)
(y_pos)

add () to [x_positions v]

add () to [y_positions v]

change [x_pos v] by ()
(columns ::custom
() / () 
() - ()
```

--- /hint --- --- hint ---

यहाँ `generate positions`{:class="block3myblocks"} ब्लॉक के लिए पूरी की गई स्क्रिप्ट है:

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
repeat (columns :: custom-arg)
+ add (x_pos) to [x_positions v]
+ add (y_pos) to [y_positions v]
+ change [x_pos v] by ((400) / ((columns :: custom-arg) - (1)
```

--- /hint ------ /hints --- --- /task ---