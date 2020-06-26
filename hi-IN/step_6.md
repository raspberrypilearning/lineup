## परिधान बदलें

फिलहाल, आपका प्रोग्राम स्प्राइट के उसी परिधान पर बार बार मोहर लगाता है, और परिधान का आकार बहुत बड़ा है।

\--- task \---

`stamp sprites`{:class="block3myblocks"} ब्लॉक में कोड जोड़ें ताकि `repeat`{:class="block3control"} के शुरू होने से पहले स्प्राइट को उपयुक्त आकार का बनाया जा सके। `stamp`{:class="block3extensions"} ब्लॉक के बाद `next costume`{:class="block3looks"} पर जाने के लिए लूप के अंदर एक ब्लॉक जोड़ें।

```blocks3
define stamp sprites (rows) (columns)
set size to (40) %
set [index v] to [1]
repeat (columns :: custom-arg)
go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
stamp
next costume
change [index v] by (1)
```

\--- /task \---

अब आप जब स्क्रिप्ट चलाते हैं, तो आपको कुछ इस तरह से दिखना चाहिए:

![
बदला हुआ_स्प्राइट](images/changed_sprites.png)

आपका प्रोग्राम सभी परिधानों को क्रम से चलाता है। आपको ग्रिड पर स्प्राइट को अनियमित स्थानों पर मोहर लगानी चाहिए, ताकि हर बार जब प्रोग्राम चलता है तो प्रत्येक परिधान उसी जगह पर दिखाई न दे।

ऐसा करने के लिए, आपको इस **एल्गोरिथम** का पालन करना होगा:

1. `Repeat`{:class="block3control"} जब तक सूची खाली न हो जाए
2. `index`{:class="block3variables"} को `1` और सूची की लंबाई के बीच किसी `random`{:class="block3operators"} संख्या पर पर सेट करें
3. स्प्राइट को आगे ले जाएँ जैसा आपने पहले किया था
4. `index`{:class="block3variables"} स्थिति की आइटम को `y_positions`{:class="block3variables"} सूची में से हटाएँ
5. `x_positions`{:class="block3variables"} सूची में से `index`{:class="block3variables"} स्थिति की मद को हटाएँ

\--- task \---

ग्रिड पर क्रमरहित स्थानों में स्प्राइट पर मोहर लगाने के लिए कोड जोड़ें।

\--- hints \--- \--- hint \---

`repeat`{:class="block3control"} लूप से पहले उसमें से `set index to 1`{:class="block3variables"} निकालें।

फिर लूप के भीतर, `set index to`{:class="block3variables"} को एक `random`{:class="block3operators"} क्रमरहित संख्या पर सेट करें जो `1` और `length of x_positions`{:class="block3variables"} के बीच की हो।

फिर `index`{:class="block3variables"} आइटम को `x_positions`{:class="block3variables"} और `y_positions`{:class="block3variables"} दोनों सूचियों में से हटाने के लिए `delete`{:class="block3variables"} का उपयोग करें।

\--- /hint \--- \--- hint \---

आपके लिए आवश्यक अतिरिक्त ब्लॉक यहाँ दिए गए हैं:

```blocks3
define stamp sprites (rows) (columns)
set size to (40) %
- set [index v] to [1]
repeat (columns :: custom-arg)
go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
stamp
next costume
- change [index v] by (1)
end

set [index v] to ()
(pick random () to ()
length of [x_positions v]
delete () of [x_positions v]

delete () of [y_positions v]
(index)
(index)
```

\--- /hint \--- \--- hint \---

आपका कोड ऐसा दिखना चाहिए:

```blocks3
define stamp sprites (rows) (columns)
set size to (40) %
- set [index v] to [1]
repeat (columns :: custom-arg)
+ set [index v] to (pick random (1) to (length of [x_positions v]))
go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
+ delete (index) of [x_positions v]
+ delete (index) of [y_positions v]
stamp
next costume
- change [index v] by (1)
```

\--- /hint \--- \--- /hints \--- \--- /task \---