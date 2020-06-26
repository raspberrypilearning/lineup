## पंक्तियाँ जोड़ें

अब जब आपके पास मोहर वाले परिधानों की एक पंक्ति बनाने के लिए कोड है, तो आपको अधिक पंक्तियाँ बनाने के लिए कोड जोड़ना चाहिए।

अपने `generate positions`{:class="block3myblocks"} ब्लॉक पर जाएँ।

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
set [x_pos v] to [-200]
repeat (columns :: custom-arg)
add (x_pos) to [x_positions v]
add (y_pos) to [y_positions v]
change [x_pos v] by (((400) / (columns)) - (1))
```

--- task ---

एक और `repeat`{:class="block3control"} लूप जोड़ें जो उतनी बार चलता है जो आप `generate positions`{:class="block3myblocks"} ब्लॉक को `rows`{:class="block3myblocks"} इनपुट के रूप में देते हैं। यहाँ दिखाए गए अनुसार `repeat`{:class="block3control"} लूप को अपनी स्क्रिप्ट में रखें:

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
+repeat (rows :: custom-arg)
set [x_pos v] to [-200]
repeat (columns :: custom-arg)
add (x_pos) to [x_positions v]
add (y_pos) to [y_positions v]
change [x_pos v] by (((400) / (columns :: custom-arg)) - (1))
end
end
```

--- /task ---

इसके बाद आपको `y_pos`{:class="block3variables"} का मान हर बार बढ़ाना होता है जब `repeat (rows)`{:class="block3control"} लूप चलता है।

इसे आप उसी रूप में करते हैं जिस रूप में आप `x_pos`{:class="block3variables"} का मान `repeat (columns)`{:class="block3control"} लूप में बढ़ाते हैं।

--- task ---

`repeat (rows)`{:class="block3control"} लूप के अंदर के कोड के अंत में, `y_pos`{:class="block3variables"} को `150`{:class="block3variables"} तक बढ़ जाना चाहिए, जो `-150`{:class="block3variables"} के अपने आरंभिक मान `300`{:class="block3variables"} से दूर है। मोहरों की प्रत्येक पंक्ति के लिए ऐसा होना चाहिए।

```blocks3
define generate positions (rows)(columns)
delete [all v] of [y_positions v]
delete [all v] of [x_positions v]
set [y_pos v] to [-150]
repeat (rows :: custom-arg)
set [x_pos v] to [-200]
repeat (columns :: custom-arg)
add (x_pos) to [x_positions v]
add (y_pos) to [y_positions v]
change [x_pos v] by (((400) / (columns :: custom-arg)) - (1))
end
+change [y_pos v] by (((300) / (rows :: custom-arg)) - (1))
end
```

--- /task ---

--- task ---

सुनिश्चित करें कि आप अपने ब्लॉकों को इनपुट के रूप में `rows`{:class="block3myblocks"} की संख्या देते हैं।

```blocks3
when flag clicked
erase all
generate positions (4) (10) ::custom
stamp sprite (4) (10) ::custom
```

--- /task ---

--- task ---

अपना कोड चलाएँ।

![मोहरों की गड़बड़ी](images/mess_stamps.png)

आपको मोहरों का एक साफ-सुथरा ग्रिड नहीं मिलेगा।

ऐसा इसलिए है, क्योंकि अभी, `stamp sprite`{:class="block3myblocks"} ब्लॉक केवल कॉलमों की कुल संख्या के लिए चलता है।

--- /task ---

--- task ---

अपनी `stamp sprites`{:class="block3myblocks"} स्क्रिप्ट को बदलें ताकि यह स्प्राइट्स की पूरी ग्रिड पर मोहर लगाने के लिए पर्याप्त बार `repeats`{:class="block3control"} का उपयोग करती है।

--- hints ---
 --- hint ---

आपको मोहरों की जो कुल संख्या चाहिए होती है वह `columns`{:class="block3myblocks"} को दी गई संख्या को `rows`{:class="block3myblocks"} को दी गई संख्या से गुणा करके प्राप्त होती है।इस अतिरिक्त ब्लॉक का उपयोग करें:

--- /hint --- --- hint ---

इस अतिरिक्त ब्लॉक का उपयोग करें:

```blocks3
((rows ::custom) * (columns ::custom))
```

--- /hint --- --- hint ---

यहाँ `stamp sprites`{:class="block3myblocks"} ब्लॉक के लिए पूरी की गई स्क्रिप्ट है:

```blocks3
define stamp sprites (rows) (columns)
set size to (40) %
+ repeat ((rows :: custom-arg) * (columns :: custom-arg))
set [index v] to (pick random (1) to (length of [x_positions v]))
go to x: (item (index) of [x_positions v]) y: (item (index) of [y_positions v]
delete (index) of [x_positions v]
delete (index) of [y_positions v]
stamp
next costume
```

--- /hint ------ /hints ---

![
आदेशित किया गया ग्रिड](images/nice_grid.png)

--- /task ---