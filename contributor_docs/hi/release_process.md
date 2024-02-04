#  रिलीज़ प्रक्रिया

## दृष्टिकोण
* हम [सेमवर](https://semver.org/) वर्जनिंग पैटर्न का पालन करते हैं, जिसका अर्थ है कि हम इस वर्जनिंग पैटर्न का पालन करते हैं: `MAJOR:MINOR:PATCH`।

## आवश्यकताएं
* Git, node.js और NPM आपके सिस्टम पर स्थापित हैं
* आप लाइब्रेरी बनाने में सक्षम हैं और रिमोट रिपॉजिटरी तक पुश एक्सेस प्राप्त कर सकते हैं
* गुप्त `NPM_TOKEN` मान दूरस्थ रिपॉजिटरी पर सेट है
* गुप्त `ACCESS_TOKEN` मान दूरस्थ रिपॉजिटरी पर सेट किया गया है

## सुरक्षा टोकन
रिलीज़ चरणों को पूरी तरह से चलाने के लिए, दो [रिपोजिटरी रहस्य](https://docs.github.com/en/actions/security-guides/encrypted-secrets#creating-encrypted-secrets-for-a-repository) होने चाहिए नीचे के रूप में सेट करें.

* पढ़ने और प्रकाशित करने के लिए टोकन बनाने के लिए [यहां](https://docs.npmjs.com/creating-and-viewing-access-tokens) चरणों का पालन करके `NPM_TOKEN` बनाया जा सकता है। टोकन जिस उपयोगकर्ता का है, उसके पास एनपीएम पर प्रोजेक्ट तक प्रकाशन की पहुंच होनी चाहिए।

* `ACCESS_TOKEN` उस उपयोगकर्ता के लिए एक व्यक्तिगत एक्सेस टोकन है जिसके पास `p5.js`, `p5.js-website`, और `p5.js-release` रिपॉजिटरी तक पहुंच है। टोकन [यहां](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) चरणों का उपयोग करके उत्पन्न किया जा सकता है। स्कोप, केवल `रेपो` और `वर्कफ़्लो` चुनें। इसके लिए एक संगठन विशिष्ट खाते का उपयोग करने की अनुशंसा की जाती है (अर्थात व्यक्तिगत खाते से नहीं) और खाते की लेखन पहुंच को केवल आवश्यक रिपॉजिटरी तक सीमित करें।

## Usage
```sh
$ git checkout main
$ npm version [major|minor|patch] # Choose the appropriate version tag
$ git push origin main
$ git push origin v1.4.2 # Replace the version number with the one just created above
```
वास्तविक रिलीज़ चरण GitHub Actions CI पर चलते हैं।

## Monitor and check results
एक बार उपरोक्त कमांड निष्पादित हो जाने के बाद, बिल्ड और रिलीज़ कार्रवाई की निगरानी p5.js GitHub रेपो पेज पर ["एक्शन" टैब](https://github.com/processing/p5.js/actions) से की जा सकती है। ऐसी Job की तलाश करें जिस पर लिखा हो "नया p5.js रिलीज़", Job पर क्लिक करने से जो चल रहा है उसका अधिक विस्तृत जॉब लॉग मिल सकता है।

![नया p5.js रिलीज़" कार्य चलाने वाले GitHub एक्शन का स्क्रीनशॉट](images/release-action.png)

एक बार काम पूरा हो जाने के बाद, लाइब्रेरी को GitHub और NPM पर जारी कर दिया जाएगा। यह देखने के लिए कि नवीनतम संस्करण जारी किया गया है, [रिलीज़](https://github.com/processing/p5.js/releases) और [NPM](https://www.npmjs.com/package/p5) पेज देखें . आपको GitHub पर ड्राफ्ट रिलीज़ देखना चाहिए, यदि आवश्यक हो तो चेंजलॉग में बदलाव करें, फिर रिलीज़ प्रकाशित करें।

जैसे ही वेबसाइट का अपना निर्माण और परिनियोजन कार्य पूरा हो जाएगा, उसे अपडेट कर दिया जाएगा, इसकी निगरानी प्रासंगिक ["कार्रवाई" पृष्ठ](https://github.com/processing/p5.js-website/actions) पर भी की जा सकती है। यदि वांछित है, और उसके बाद नवीनतम संस्करण संख्या के लिए वेबसाइट पर ["डाउनलोड" पृष्ठ](https://p5js.org/download/) देखें।

सीडीएन को अपडेट होने में थोड़ा अधिक समय (एक या दो दिन) लगेगा लेकिन रिलीज होने पर वे स्वचालित रूप से एनपीएम से हट जाएंगे इसलिए किसी विशेष कार्रवाई की आवश्यकता नहीं है।


## असल में क्या हो रहा है
GitHub एक्शन ["नया p5.js रिलीज़"](../.github/workflows/release.yml) एक टैग पर ट्रिगर होता है जो पैटर्न `v*.*.*` से मेल खाता है जो `npm version ___` आदेश से बनाया जाता ह .


एक बार ट्रिगर होने पर, यह निम्नलिखित चरण चलाएगा:
1. रिपॉजिटरी को क्लोन करें, नोड.जेएस सेटअप करें, संस्करण संख्या निकालें, `एनपीएम` के साथ निर्भरताएं स्थापित करें, और `एनपीएम टेस्ट` के साथ परीक्षण चलाएं।
2. रिलीज़ फ़ाइलें बनाएं जिन्हें GitHub रिलीज़ पर अपलोड किया जाएगा।
3. GitHub पर एक रिलीज़ बनाएं और NPM पर नवीनतम संस्करण प्रकाशित करें।
4. वेबसाइट फ़ाइलें अद्यतन करें
1. वेबसाइट रिपॉजिटरी को क्लोन करें
2. `data.json` और `data.min.json` को सही स्थान पर कॉपी करें
3. `p5.min.js` और `p5.sound.min.js` को सही स्थान पर कॉपी करें
4. `data.yml` फ़ाइल को नवीनतम संस्करण संख्या के साथ अद्यतन करें
5. `en.json` फ़ाइल को `data.min.json` के आधार पर अपडेट करें
6. परिवर्तनों को प्रतिबद्ध करें और वेबसाइट रिपॉजिटरी में वापस भेजें
5. बोवर फ़ाइलें अद्यतन करें
1. बोवर रिलीज़ रिपॉजिटरी का क्लोन बनाएं
2. सभी लाइब्रेरी फ़ाइलों को सही स्थान पर कॉपी करें
3. परिवर्तनों को प्रतिबद्ध करें और वेबसाइट रिपॉजिटरी में वापस भेजें

सिद्धांत रूप में, हम एक ही स्थान पर चलने के लिए यथासंभव अधिक से अधिक चरणों पर ध्यान केंद्रित करने का प्रयास करते हैं, अर्थात। सीआई वातावरण में. यदि एक नया चरण जो केवल रिलीज़ पर चलाया जाता है, आवश्यक है, तो इसे संभवतः सीआई वर्कफ़्लो में परिभाषित किया जाना चाहिए, न कि बिल्ड कॉन्फ़िगरेशन के भाग के रूप में।

## परिक्षण
चूंकि रिलीज़ चरण सीआई में चलाए जाते हैं, इसलिए उनका परीक्षण करना कठिन हो सकता है। स्थानीय स्तर पर चरणों को चलाने का परीक्षण करने के लिए [एक्ट](https://github.com/nektos/act) का उपयोग करना संभव है (और विकसित होने के दौरान उनका परीक्षण कैसे किया गया था) लेकिन वर्कफ़्लो परिभाषा में कुछ अस्थायी संशोधन की आवश्यकता है, हम करेंगे यहां मोटे तौर पर दस्तावेजीकरण करें क्योंकि समय के साथ सटीक चरण बदल जाएंगे।

परीक्षण चरण नहीं चलेंगे क्योंकि मोचा क्रोम परीक्षण चलाने के लिए सभी सिस्टम आवश्यकताएँ मौजूद नहीं हैं। शेष परिवेश को स्थापित करने से पहले कुछ सिस्टम निर्भरताओं को `apt` के साथ स्थापित करने की आवश्यकता होगी। त्रुटि संदेशों पर नज़र रखें जिससे यह जानकारी मिलनी चाहिए कि कौन से पैकेज गायब हैं।

गलती से अनपेक्षित परिवर्तनों को आगे बढ़ाने से बचने के लिए दूरस्थ रिपॉजिटरी में परिवर्तनों को आगे बढ़ाने से संबंधित कदमों पर टिप्पणी की जानी चाहिए।