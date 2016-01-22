# 磨練閱讀程式技巧，不受黑盒限制




基於黑盒子化的軟體元件封裝進行開發，已經是廣泛接受而且流行的方式，不過成也黑盒，敗或許也在黑盒。世上沒有完美的黑盒子，開放原始碼軟體讓我們有機會修正其中的瑕疵，也可加以改造，使它的威力更為強大。



物件導向的設計方法，也促成了元件化軟體開發模式的風行。當你越是重視重複使用、多型、封裝、介面化等設計的觀念時，就可能會在不知不覺間，養成以設計黑盒子的方式，來設計自己所開發的軟體模組，以及用黑盒子的方式，來看待他人所設計的軟體模組。

###封印了軟體的複雜度，開發產能大躍進
人們將軟體模組打造成黑盒子的型態，是為了將軟體高度的複雜度，封印在這個黑盒子中。舉凡那些高度耦合的、容易有所變動的、不欲外界知悉的「黑暗事物」，一律將它們封鎖在黑色的盒子之中。

克服了對開發者威脅甚大的複雜度之後，軟體的開發生產力，不僅將大幅躍升，而且與日俱進。漸漸的，開發者反而要學習試著不去探索、碰觸黑盒子中的事物，甚至要對它們視而不見。因為只有在它不曝露內部實作及結構的情況下，才能被運用得更好。同樣的，也只有在不知道內部實作及結構的情況下，才能善用它。

對於類別庫或元件庫的建造者而言，打造出內容越來越豐富、支援越來越廣泛、而威力也越來越強大的類別及元件，不僅提升開發生產力，同時也讓程式人從事開發的門檻降低。

許多剛入門的程式人，只需要知道有什麼可用的元件，接著將它們兜在一塊，便可以輕易地開發出許多應用程式。這當然是軟體開發模式的一大躍進──開發速度更快、而且更容易。

###黑盒子也可能成為專案的地雷
完美的黑盒子很棒，但是幾乎不存在。你所使用的黑盒子都難免有缺陷。它或許內藏臭蟲，或許效率表現不符合你的期待。黑盒子本身為了隱藏內部實作，會設下一道又一道的防線，將你所能觸及的範圍，阻擋於黑盒子之外。因此，身為黑盒子的使用者，當你所面對的是一個有缺陷的黑盒子時，通常只能徒呼負負，望著它發呆了。

開發者操駕著十分先進的開發工具高速前進，但一旦遇上了意料之外的阻礙時，卻時常只能在原地踏步、難以往前再進半尺。這無疑是黑盒子化後的軟體開發，最常遇到的問題，程式人只是元件的使用者，當元件發生問題時，多半只能束手無策，而這也會造成開發進度嚴重的遲滯，甚至讓系統無法如預期完成，黑盒子反而成了問題的根源所在。

###問題可能是使用的方式不正確
另一方面，黑盒子不僅封印了內部的結構及實作方式，有時它某種程度將自身的運作方式，甚至是相關的知識給封鎖於內部。許多情況下，不懂得相關運作方式及知識，仍能在一知半解的情況下使用這樣的元件。但有時候使用黑盒子元件造成的障礙，並不在黑盒子本身，而是在於使用它的方式並不正確。

就拿關聯式資料庫系統做為例子，對許多程式人而言，它就是一個極為大型的黑盒子。他們幾乎不明白關聯式資料庫究竟是如何實作的，也不知道它是如何有效率地儲存資料，更不知道它是透過什麼樣的方法，提供諸如查詢、排序之類的操作。

對程式人來說，資料庫系統是個大型黑盒，與這個黑盒子溝通的介面，便是高度抽象化的SQL。SQL封裝了人們操作資料的需求，並以一個足夠彈性且與底層實作方式獨立的語言加以表述。這當然簡化了人們在開發應用程式時所需撰寫用的程式以操作資料，也降低了撰寫此類程式的門檻，但是，對於資料庫運作方式不熟悉的程式人，往往又十分容易寫出效能低落的SQL述句。

單看SQL述句的邏輯本身並無瑕疵，但因為程式人不了解SQL述句的特性，造成了執行效能低落。這樣的問題隱藏在系統中，實在難以察覺，因為它邏輯上是對的、或是看似是對的。這使得黑盒子造成的障礙更為嚴重。

大量倚靠黑盒子所衍生出來的問題──不僅遇上了無法解決，甚至還可能會因為對它的不了解，而發生誤用。

這像是一個兩難的局面。黑盒子讓程式人們又愛又恨，他們愛用包裝成為黑盒子的現成元件，因為它能讓生產力大增。但當問題出在黑盒子化的元件時，程式人又會氣得牙癢癢的，因為明明知道問題出在哪裏，卻又無可施力之處，因為完全不知道黑盒子是如何實作，而且即使知道如何實作，也無法加以修改。

###開放原始碼的黑盒子，使我們不致望盒興嘆
著名資訊技術作家侯捷曾用「軟體是否有開放原始碼」，來做為軟體究竟是黑盒子還是白盒子的分野，便是站在盒子是否能被打開或看穿的觀點之上。當我們手上握有元件的原始碼時，當問題出在元件時，便有機會自行修正元件的問題，而不致於只能望盒興嘆，這正是使用開放原始碼軟體的優勢所在。

軟體模組究竟是不是一具黑盒子，其實我並不認為是單從有無開放原始碼來論斷。黑盒子化的包裝是一種設計的方式，也是一種看待軟體模組的方式。即使是開放原始碼的軟體，仍然可以用黑盒子的角度來加以對待，只不過我們仍然保有將這個黑盒子拆開的機會。

在大多數的應用情境下，我們仍將開放原始碼的軟體元件視為黑盒子，並且透過它的介面與之相接，並不會將手伸進這黑盒之中。畢竟這黑色的外盒，作用在於保護我們免於觸及盒內的複雜事物，並且與之相隔絕。

但是，當我們發現這黑盒存在瑕疵時，憑藉著開放的原始碼，便有機會打開盒子，並且自行修正黑盒中的潛在瑕疵，不再束手無策。
有了開放的原始碼，你甚至可以自行改造黑盒子，使它的威力更為強大。

###有能力拆解黑盒子，才不會受盒子限制
能不能拆解黑盒子，有時不僅和有沒有開放原始碼的形式有關，也和程式人本身的能力有關。侯捷曾經說過：「源碼之前了無祕密」。的確，當你手上已經持有軟體所有的原始碼時，看似所有奧祕皆已為你所掌握。

不過，原始碼的閱讀技巧，人人各有功力，高下不同，每個讀者能懂的程度，自然也就深淺不一。而在原始碼之外，還有更多內隱的東西，不易單靠原始碼，便理解箇中奧妙，例如演算法、數學，或者是專業的領域知識，並不是片面透過原始碼，便能一窺堂奧的。

當我們試著拆解黑盒子時，伴隨著需要補充相關的領域知識，才能更全面地理解原始碼的運作方式及行為。

基於黑盒子化的軟體元件封裝進行開發，已經是廣泛接受而且流行的方式，而且對於生產力絕對是大有助益。程式人必須學著以看待黑盒子的方式來設計、使用軟體模組。

不過成也黑盒，敗或許也在黑盒。世上沒有完美的黑盒子，在開發時，察覺到問題出在黑盒子本身時，恐怕都是許多程式人最大的惡夢。在這個時候，突顯出開放原始碼軟體的優點，它賦予我們一把打開黑盒子的鑰匙。

但想要善用這開放原始碼的元件，程式人必須磨練閱讀他人程式碼的技巧，才能不受黑盒子限制，同時又能加以運用。

## Reference
- http://www.ithome.com.tw/node/50699