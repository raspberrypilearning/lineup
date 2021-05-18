## अपने स्प्राइट को छिपाएँ

अब मोहरों की भीड़ के बीच अपने स्प्राइट को छिपाने का समय है। फिलहाल स्प्राइट किसी एक मोहर को ओवरलैप करता है।

![ओवरलैप](images/overplap-annotated.png)

\--- task \---

इसलिए यह नहीं होता है, अपनी मोहर के लूप को एक बार कम चलाएँ `(rows * columns) - 1`{:class="block3operators"}

```blocks3
define stamp sprites (rows) (columns)
set size to (40) %
+repeat (((rows :: custom-arg) * (columns :: custom-arg)) - (1))
set [index v] to (pick random (1) to (length of [x_positions v]))
go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
delete (index) of [x_positions v]
delete (index) of [y_positions v]
stamp
next costume
```

\--- /task \---

यदि आप अब स्क्रिप्ट को चलाते हैं, तो आप देख सकते हैं कि आपका स्प्राइट अभी भी एक मोहर के साथ ओवरलैप करता है और आपके ग्रिड में एक छेद है। और `x_positions`{:class="block3variables"} और `y_positions`{:class="block3variables"} सूचियों में, एक निर्देशांक स्थिति बाकी बची है।

\--- task \---

गेम के इस हिस्से को समाप्त करने के लिए, स्क्रिप्ट के `when flag clicked`{:class="block3events"} खंड में जाएँ।

```blocks3
when flag clicked
erase all
generate positions (4) (10) ::custom
stamp sprites (4) (10) ::custom
```

\--- no-print \---

यहां एक एनीमेशन दिखाया गया है जो होना चाहिए:

![एनीमेशन](images/demo_1.gif)

\--- /no-print \---

गेम के आरंभ में, स्प्राइट एक बड़े आकार में दिखाई देना चाहिए और कहना चाहिए कि "मुझे खोजें"। फिर स्प्राइट को आपके द्वारा उसके लिए छोड़ी गई खाली जगह में मोहरों के बीच खुद को छिपा लेना चाहिए।

देखें कि क्या आप यह पता लगा सकते हैं कि यह कैसे करना है, और अगर आपको मदद चाहिए हो तो नीचे दिए गए संकेतों का उपयोग करें।

\--- hints \--- \--- hint \---

यह वही करने की आवश्यकता है:

1. अपने स्प्राइट को `x:0 y:0`{:class="block3motion"} पर भेजें
2. स्प्राइट को `front`{:class="block3looks"} पर लाएँ और इसके आकार को `size to 100%`{:class="block3looks"} पर सेट करें
3. `Say 'Find me' for two seconds `{:class="block3looks"}
4. `Go back one layer`{:class="block3looks"}
5. स्प्राइट के आकार को `40%`{:class="block3looks"} पर सेट करें
6. सूचियों में अंतिम बचा हुआ स्थिति पर जाएं

\--- /hint \--- \--- hint \---

आपके लिए आवश्यक अतिरिक्त ब्लॉक यहाँ दिए गए हैं:

```blocks3
when flag clicked
erase all
generate positions (4) (10) ::custom
stamp sprites (4) (10) ::custom

go to x: (0) y: (0)

go [backward v] (1) layers

go to [front v] layer

set size to (100) %

set size to (40) %

say [] for (2) seconds
item (1 v) of [x_positions v]
item (1 v) of [y_positions v]
go to x: () y: ()
```

\--- /hint \--- \--- hint \---

पूरी की गई `when flag clicked`{:class="block3events"} स्क्रिप्ट यहाँ दी गई है:

```blocks3
when flag clicked
erase all
generate positions (4) (10) ::custom
stamp sprites (4) (10) ::custom
+go to x: (0) y: (0)
+go to [front v] layer
+set size to (100) %
+say [Find me] for (2) seconds
+go [backward v] (1) layers
+set size to (40) %
+ go to x: (item (1 v) of [x_positions v]) y: (item (1 v) of [y_positions v])
```

\--- /hint \--- \--- /hints \--- \--- /task \---