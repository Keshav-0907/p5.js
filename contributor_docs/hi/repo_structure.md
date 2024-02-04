# हमारा कोड कहा रहता है


व्यापक p5.js प्रोजेक्ट में इसके अलावा कुछ रिपॉजिटरी शामिल हैं:

- **[p5.js](https://github.com/processing/p5.js)**: इस रिपॉजिटरी में p5.js लाइब्रेरी के लिए सोर्स कोड है। [उपयोगकर्ता-सामना करने वाला p5.js संदर्भ मैनुअल](https://p5js.org/reference/) भी इस स्रोत कोड में शामिल [JSDoc](https://jsdoc.app/) टिप्पणियों से उत्पन्न होता है। इसका रखरखाव [Qianqian Ye](https://github.com/qianqianye) और [स्टीवर्ड्स](https://github.com/processing/p5.js#stewards) के एक समूह द्वारा किया जाता है।

- **[p5.js-website](https://github.com/processing/p5.js-website)**: इस रिपॉजिटरी में [p5.js website](http://p5js.org), संदर्भ मैनुअल के अपवाद के साथ। इसका रखरखाव [Qianqian Ye](https://github.com/qianqianye), [केनेथ लिम](https://github.com/limzykenneth), और [स्टीवर्ड्स]([https://github](https://github.com/processing/p5.js-website#stewards)) के एक समूह द्वारा किया जाता है। 


- **[p5.js-sound](https://github.com/processing/p5.js-sound)**: इस रिपॉजिटरी में p5.sound.js लाइब्रेरी शामिल है। इसका रखरखाव [जेसन सिगल](https://github.com/wherewasaguy) द्वारा किया जाता है।

- **[p5.js-web-editor](https://github.com/processing/p5.js-web-editor)**: इस रिपॉजिटरी में [p5.js वेब एडिटर]( https://editor.p5js.org). इसका रखरखाव [कैसी ताराकाजियन](https://github.com/catarak) द्वारा किया जाता है।

- ऊपर सूचीबद्ध नहीं की गई अन्य ऐड-ऑन लाइब्रेरीज़ में आमतौर पर अपने स्वयं के भंडार और अनुरक्षक होते हैं और सीधे p5.js प्रोजेक्ट द्वारा बनाए नहीं रखे जाते हैं।


## रिपॉजिटरी फ़ाइल संरचना

यहाँ बहुत सारी फ़ाइलें हैं! यहां एक संक्षिप्त अवलोकन दिया गया है. यह भ्रमित करने वाला हो सकता है, लेकिन आरंभ करने के लिए आपको रिपॉजिटरी की प्रत्येक फ़ाइल को समझने की आवश्यकता नहीं है। हम अनुशंसा करते हैं कि एक क्षेत्र से शुरुआत करें (उदाहरण के लिए, कुछ इनलाइन दस्तावेज़ों को ठीक करना), और अधिक खोज करने के लिए बाहर की ओर काम करें। लुइसा परेरा का [लुकिंग इनसाइड p5.js](https://www.luisapereira.net/teaching/materials/processing-foundation) p5.js वर्कफ़्लो में उपयोग किए गए टूल और फ़ाइलों का एक वीडियो टूर भी देता है।

- 📁`contributor_docs/` में ऐसे दस्तावेज़ शामिल हैं जो योगदानकर्ताओं के लिए प्रथाओं और सिद्धांतों की व्याख्या करते हैं
- 📁`docs/` में वास्तव में दस्तावेज़ शामिल नहीं हैं! बल्कि, इसमें [ऑनलाइन संदर्भ मैनुअल](https://p5js.org/reference/) *जेनरेट* करने के लिए उपयोग किया गया कोड शामिल है।
- 📁`lib/` में एक खाली उदाहरण और p5.sound ऐड-ऑन शामिल है, जिसे समय-समय पर [p5.js-sound रिपॉजिटरी](https://github.com/processing/p5.js) से पुल अनुरोध के माध्यम से अपडेट किया जाता है। यह वह जगह भी है जहां निर्मित p5.js लाइब्रेरी को [ग्रंट](https://gruntjs.com/) का उपयोग करके एकल फ़ाइल में संकलित करने के बाद रखा जाता है। जब आप पुल अनुरोध करते हैं तो इसे GitHub रिपॉजिटरी में जांचने की आवश्यकता नहीं है।
- 📁`src/` में लाइब्रेरी के लिए सभी स्रोत कोड शामिल हैं, जो शीर्ष रूप से अलग-अलग मॉड्यूल में व्यवस्थित हैं। यदि आप p5.js बदल रहे हैं तो आप इसी पर काम करेंगे। आपको अपना रास्ता खोजने में मदद करने के लिए अधिकांश फ़ोल्डरों के अंदर अपनी स्वयं की readme.md फ़ाइलें होती हैं।
- 📁`tasks/` में ऐसी स्क्रिप्ट्स होती हैं जो p5.js के नए संस्करणों के निर्माण, परिनियोजन और रिलीज़ से संबंधित स्वचालित कार्य करती हैं।
- 📁`tests/` में यूनिट परीक्षण शामिल हैं जो यह सुनिश्चित करते हैं कि परिवर्तन किए जाने पर लाइब्रेरी सही ढंग से कार्य करती रहे।
- 📁`utils/` में रिपॉजिटरी के लिए उपयोगी अतिरिक्त फ़ाइलें हो सकती हैं, लेकिन आम तौर पर आप इस निर्देशिका को अनदेखा कर सकते हैं।


## मिश्रित
- 📁[`contributor_docs/`](https://github.com/processing/p5.js/tree/main/contributor_docs) फ़ोल्डर में अन्य फ़ाइलें हैं जिन्हें आप एक्सप्लोर कर सकते हैं। वे इस परियोजना के तकनीकी और गैर-तकनीकी दोनों विशिष्ट क्षेत्रों में योगदान देने से संबंधित हैं।
- [लुकिंग इनसाइड p5.js](https://www.luisapereira.net/teaching/materials/processing-foundation) p5.js डेवलपमेंट वर्कफ़्लो में उपयोग किए जाने वाले टूल और फ़ाइलों का एक वीडियो टूर है।
- [द कोडिंग ट्रेन का यह वीडियो](https://youtu.be/Rr3vLyP1Ods) :train::rainbow: p5.js में तकनीकी योगदान के साथ शुरुआत करने का एक सिंहावलोकन देता है।
- p5.js [डॉकर छवि](https://github.com/toolness/p5.js-docker) को [Docker](https://www.docker.com/) में माउंट किया जा सकता है और p5 विकसित करने के लिए उपयोग किया जा सकता है .js को [नोड](https://nodejs.org/) जैसी आवश्यकताओं की मैन्युअल स्थापना की आवश्यकता के बिना या किसी भी तरह से होस्ट ऑपरेटिंग सिस्टम को प्रभावित किए बिना, डॉकर की स्थापना के अलावा।
- p5.js लाइब्रेरी के लिए निर्माण प्रक्रिया एक [JSON डेटा फ़ाइल](https://p5js.org/reference/data.json) उत्पन्न करती है जिसमें p5.js की सार्वजनिक एपीआई होती है और इसका उपयोग स्वचालित टूलींग में किया जा सकता है, जैसे जहाँ तक एक संपादक में p5.js विधियों को स्वतः पूर्ण करने का प्रश्न है। यह फ़ाइल p5.js वेबसाइट पर होस्ट की गई है, लेकिन यह रिपॉजिटरी के भाग के रूप में शामिल नहीं है।