## पंक्ति पर मोहर लगाएँ

अब तक आपके पास दोनों सूचियों में दस-दस मान हैं। अब सूचियों में संगृहीत स्टेज निर्देशांकों में कुछ परिधानों पर मोहर लगाएँ।

--- task ---

अपने प्रोजेक्ट में **कलम** विस्तार जोड़ें।

[[[generic-scratch3-add-pen-extension]]]

--- /task ---

--- task ---

एक नया ब्लॉक बनाएं और इसका नाम `stamp sprites`{:class="block3myblocks"} रखें। दूसरे कस्टम ब्लॉक की तरह इस ब्लॉक के लिए भी `rows`{:class="block3myblocks"} और `columns`{:class="block3myblocks"} नाम के दो नंबर इनपुट चाहिए।

```blocks3
define stamp sprites (rows) (columns)
```

--- /task ---

--- task ---

`index`{:class="block3variables"} नामक एक नया वेरिएबल तैयार करें जिसके साथ उन सूचियों में स्थितियों को ट्रैक किया जा सकता है जिन्हें आपका प्रोग्राम पढ़ रहा हो। आरंभ करने के लिए, प्रत्येक सूची की पहली पद को लाने के लिए `index`{:class="block3variables"} को `1`{:class="block3variables"} पर सेट करें।

```blocks3
define stamp sprites (rows) (columns)
+ set [index v] to [1]
```

--- /task ---

--- task ---

`stamp sprites`{:class="block3myblocks"} ब्लॉक को सूची में निर्देशांक के प्रत्येक जोड़े के लिए एक स्प्राइट पर मोहर लगानी चाहिए। ऐसा करने के लिए, ब्लॉक को एक `repeat`{:class="block3variables"} लूप की ज़रूरत होती है जो प्रत्येक क़तार के लिए एक बार चलता है।

```blocks3
define stamp sprites (rows) (columns)
set [index v] to [1]
+ repeat (columns :: custom-arg)
```

--- /task ---

--- task ---

`repeat`{:class="block3variables"} लूप के भीतर:

- स्प्राइट को `x_positions`{:class="block3variables"} और `y_positions`{:class="block3variables"} सूचियों में `index`{:class="block3variables"} स्थिति में ले जाएँ
- स्प्राइट पर `Stamp`{:class="block3extensions"} का उपयोग करें
- `index`{:class="block3variables"} को `1`{:class="block3variables"} से बदलें

--- hints ---
 --- hint ---

`repeat`{:class="block3variables"} लूप के भीतर, एक `go to x: y:`{:class="block3motion"} ब्लॉक जोड़ें। इस ब्लॉक में `x`{:class="block3motion"} स्थिति को `x_positions`{:class="block3variables"} के `index`{:class="block3variables"} पर सेट किया जाना चाहिए और `y`{:class="block3motion"} स्थिति को `y_positions`{:class="block3variables"} के `index`{:class="block3variables"} पर सेट किया जाना चाहिए। फिर स्प्राइट पर `stamp`{:class="block3extensions"} कोड जोड़ें। अंत में, `index`{:class="block3variables"} को 1 से बढ़ाने के लिए कोड जोड़ें।

--- /hint --- --- hint ---

इन ब्लॉक्स की आपको आवश्यकता होगी:

```blocks3
define stamp sprites (rows) (columns)
set [index v] to [1]
repeat (columns :: custom-arg)
end

change [index v] by (1)
(index) 
(index) 
go to x: () y: ()
(item ()of [y_positions v])
(item ()of [x_positions v])
stamp
```

--- /hint --- --- hint ---

यहाँ `stamp sprites`{:class="block3myblocks"} ब्लॉक के लिए पूरी की गई स्क्रिप्ट है:

```blocks3
define stamp sprites (rows) (columns)
set [index v] to [1]
repeat (columns :: custom-arg)
+ go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
+ stamp
+ change [index v] by (1)
```

--- /hint ------ /hints --- --- /task ---

--- task ---

हर बार खेल शुरू होने पर स्टेज को खाली करने के लिए `when flag clicked`{:class="block3control"} ब्लॉक के नीचे `erase all`{:class="block3extensions"} को जोड़ें। फिर `when flag clicked`{:class="block3control"} स्क्रिप्ट के नीचे `stamp sprites`{:class="block3myblocks"} को जोड़ें ताकि आप अपने नए कोड का परीक्षण कर सकें।

```blocks3
when flag clicked
erase all
generate positions (1) (10) ::custom
stamp sprite (1) (10) ::custom
```

--- /task ---

--- task ---

हरे झंडे पर क्लिक करें । आपको कुछ इस तरह की चीज़ दिखनी चाहिए, जो इस पर निर्भर होगा कि आपके स्प्राइट का परिधान कौन सा है:

![मोहर वाले स्प्राइट](images/stamped_sprites.png)

--- /task ---