---
назив: "Binary"
опис: Дубок преглед бинарних и битних оператора.
---

## Заслуге

Ово је из упутства на SA-MP форумима. Аутор је **Кајозаур**.

## Шта је бинарни систем?

Бинарни систем је бројни систем који користи два уникатна симбола за представљање бројева. Док уобичајени децимални систем користи десет цифара (**основа 10**), бинарни систем користи само 0 и 1. Ово може звучати бескорисно у свакодневном животу, али је бинарни систем одсуствен када се ради о рачунарима. Рачунари на свом најнижем нивоу врше све своје израчунавања манипулирањем тока електричне енергије да би показали стања укључено и искључено. То је управо оно што је бинарни систем, само многи прекидачи укључени и искључени. Ово је врста алиеног концепта за већину људи, па да погледамо децимални и бинарни систем један поред другог.

Децимални (base 10)

```c
0
1
2
3
4
5
6
7
8
9
10
11
12
13
```

Бинарни (Base 2)

```c
0 //0
1 //1
10 //2
11 //3
100 //4
101 //5
110 //6
111 //7
1000 //8
1001 //9
1010 //10
1011 //11
1100 //12
1101 //13
```

Погледајући оба система један поред другог, приметићете да се понашају тачно исто. Када достигнете последњи доступан број, морате прећи на друго место. Та места у бинарном систему се називају битови (бинарни бројеви) и једноставно су степени два; као и места у децималном систему која су степени десет. Да бисмо то доказали, погледајмо број 13 у стандардној нотацији.

**НАПОМЕНА:** '^' је степен у следећим примерима, а не битно исклучива операција (коју ћемо покрити касније).

Decimal (base 10)

```c
13

//које једнако

1 * (10^1) + 3 * (10^0)

//које једнако

10+3

//које једнако

13
```

Binary (base 2)

```c
1101

//које једнако

1 * (2^3) + 1 * (2^2) + 0 * (2^1) + 1 * (2^0)

//које једнако

8+4+0+1

//које једнако

13
```

Можемо видети из претходног примера да ако је бит постављен на 0, можемо га игнорисати и наставити; на крају крајева, све помножено са 0 биће 0. Претходни пример је био мало прекомпликован и само сам покушао да будем потпуно јасан. Када претварате из бинарног, све што заиста треба да вам буде брига је да саберете степене свих битова који су укључени.

Ево 12 степени броја 2 које се могу сетити:

```c
4096,2048,1024,512,256,128,64,32,16,8,4,2,1
```

Ако ништа не знате о раду са степенима, ово вероватно уопште нема смисла за вас. Степен је број помножен сам са собом x пута. Са тим информацијама на уму, претходна листа степених бројева вероватно има више смисла; осим броја 1. Можда вас занима зашто је 2 на степен 0 резултат 1, на то могу рећи да је тако једноставно.

```c
2^1 = 2, 2^3 = 4, 2^4 = 8
```

Можемо видети да када се крећемо удесно, наша претходна вредност се множи са 2; тако да је безбедно претпоставити да када се крећемо улево, наша нова вредност је само претходни број подељен са 2. Са овим на уму, можете видети како можемо добити да је 2 на нулту степен једнако 1. Ако ово није довољно задовољавајуће, сигуран сам да можете наћи више доказа на **\*\***. Са свим тим речено, дајте да погледамо још један пример, и да направимо га мало компликованијим!

```c
111011001011111000 //242424

//Запамтите, игноришите битове који нису укључени.

1 * (2^17) = 131072

1 * (2^16) = 65536

1 * (2^15) = 32768

1 * (2^13) = 8192

1 * (2^12) = 4096

1 * (2^9) = 512

1 * (2^7) = 128

1 * (2^6) = 64

1 * (2^5) = 32

1 * (2^4) = 16

1 * (2^3) = 8


131072+65536+32768+8192+4096+512+128+64+32+16+8
=
242424
```

Запамтите када конвертујете: Прваи степен је 0, па немојте направити грешку као кад видите 18. место као 2^18. Заиста постоји 18 степени, али укључује степен 0, тако да 17 је заиста највиши степен.

### Дубљи увид у битове

Већина програмских језика дозвољава различите типове података који обухватају различите количине битова који могу бити коришћени за складиштење информација; међутим, pawn је језик без типа са 32 бита. Ово значи да ће pawn увек имати доступних 32 бита за складиштење информација. Шта се дешава када имате превише информација? Одговор на ово питање лежи у потписаним и непотписаним целим бројевима.

#### Потписани цели бројеви

Да ли сте икада забележили да када цео број у pawn превише велик, постаје негативан? Ова "замотуљена" појава настаје када пређете максималну вредност у pawn, која је:


```c
2^31 - 1 //Степен, а не битно искључив. Такође, -1 је зато што рачунамо 0 (постоји 2.147.483.648 вредности, али то је са 0, По суштини 2,147,483,647 је максимум).

//што значи

2,147,483,647

//што у бинарном облику изгледа као

1111111111111111111111111111111 //31 бит - сви укључени
```

Можда се питате зашто је ТО максимална вредност, а не 2^32-1 (4,294,967,295). Ту улазе потписани и не потписани цели бројеви. Потписани цели бројеви имају могућност складиштења негативних вредности, где не потписани цели бројеви не. Ово можда звучи као да се одвајам од питања, али вас уверавам да нисам. Разлог зашто максимални цео број није 2^32-1 је зато што се 32. бит користи као врста прекидача за негативне и позитивне вредности. Ово се зове MSB (Најзначајнији бит); ако је MSB укључен, број ће бити негативан, ако је искључен, број је позитиван. Помало једноставно, зар не?

Пре него што покажем неколико негативних вредности, треба да објасним како су негативне вредности представљене у програму Pawn. Pawn користи систем који се зове 2-ова комплементарна репрезентација да би представио негативне вредности, што у основи значи да преврнете сваки бит у вашем броју и додајте 1 новом броју како бисте га направили негативним.

Хајде да погледамо неколико негативних вредности док је ова идеја још у вашој глави:

```c
11111111111111111111111111111111 // свих 32 бита укључено

//једнако

-1

//и

11111111111111111111111111111110

//једнако

-2

//и крајње

10000000000000000000000000000000

//једнако

-2147483648
```

Видиш, сви негативни бројеви једноставно су оригинални позитивни број са свим његовим битовима преврнутим и повећаним за један. Ово је врло јасно са нашим последњим примером, пошто је највиши ПОЗИТИВАН број 2147483647.

Из овога можемо видети да је опсег бројева у павну заиста:

```c
&#8722;2^31 to +2^31 − 1
```

#### Непотписани цели бројеви

У павну не постоје непотписани цели бројеви, али ово додајем како би било избалансирано. Једина разлика између потписаних и непотписаних целих бројева је у томе што непотписани цели бројеви не могу чувати негативне вредности; Цели бројеви и даље преврћу, али се враћају на 0, а не на негативну вредност.

## Бинарни оператори

Бинарни оператори вам омогућавају манипулисање појединачним битовима у образцу битова. Погледајмо списак доступних оператора битова.

- Аритметичко померање бита: `>>`, и `<<`
- Логичко померање бита: `>>>`
- НЕ битова (познато и као комплемент): `~`
- И битова: `&`
- ИЛИ битова: `|`
- ИСКЛУЧИВО-ILI битова (познато и као искључиво-или): `^`

### И битова

**НАПОМЕНА:** Не треба мешати са логичким оператором И '&&'

Бинарно И једноставно примењује логичко И операцију над битовима на сваком месту у броју у бинарном облику. Ово звучи мало збуњујуће, па да погледамо како то изгледа у пракси!

```c
1100 //12
&
0100 //4
=
0100 //4, јер оба имају "100" у њима (што представља број 4)
```

То је било мало једноставно, да погледамо мало тежи:

```c
10111000 //184
&
01001000 //72
=
00001000 //8
```

Погледајући примере, требало би вам прилично јасно шта овај оператор ради. Он поређује два сета битова заједно, ако оба деле бит вредности 1, резултат ће имати исти бит укључен. Ако уопште не деле ниједан бит, онда је резултат 0.

### Битовски ИЛИ

**НАПОМЕНА:** Немојте га помешати са логичким ИЛИ оператором '||'

Битовски ИЛИ ради скоро исто као и битовски И. Једина разлика између ова два је што битовски ИЛИ треба само да један од два битна образца има укључен бит како би резултат имао исти бит укључен. Погледајмо неколико примера!

```c
1100 //12
|
0100 //4
=
1100 //12.
```

Да погледамо још један пример.

```c
10111000 //184
|
01001000 //72
=
11111000 //248
```

Мислим да је ово прилично јасно објашњено. Ако један од бројева има укључен бит, и резултирајући број ће такође имати тај бит укључен.

### Битни XOR

Овај оператор је мало сличан оператору битног ИЛИ, али постоји мала разлика. Погледајмо исти пример који смо користили у делу о битном ИЛИ и видимо да ли можете приметити разлику.

```c
1100 //12
^
0100 //4
=
1000 //8.
```

и крај:

```c
10111000 //184
^
01001000 //72
=
11110000 //240
```

### Побитно НЕ

Овај оператор окреће сваки бит у битном обрасцу, претварајући све 1 у 0 и обрнуто.

```c
~0
=
11111111111111111111111111111111 //-1

//и

~100 //4
=
11111111111111111111111111111011 //-5

//и

~1111111111111111111111111111111 //2147483647 (не треба мешати са -1, који има 32 бита, не 31)
=
10000000000000000000000000000000 //-2147483648 (32. бит укључен)
```

Ако не разумете зашто су негативне вредности као да су "обрнуте", молим вас прочитајте одељак о потписаним целим бројевима.

### Померање битова

Померање битова ради тачно оно што бисте замислили; помера битове у броју ка одређеном правцу. Ако се сећате раније у чланку поменуо сам да ПАУН има одређен опсег меморије (32 бита који могу бити коришћени за складиштење). Шта се дешава када померите број изван тог опсега? Одговор на ово питање лежи у томе који оператор померања користите, и у којем правцу вршите померање.

**НАПОМЕНА:** У следећим примерима, сви бинарни бројеви биће написани у целости (свих 32 бита) како би се избегле било какве забуне.

#### Аритметичка померања

#### Десно померање

Сви битови у броју се померају x пута удесно када користите овај оператор. Хајде да брзо погледамо један једноставан пример.

```c
00000000000000000000000000001000  //8
>>
2

=

00000000000000000000000000000010 //2
```

Можете видети из претходног примера да су сви битови помакнути удесно за два места, и два нула су додата на леву страну као пуни. Ове две нуле заиста су вредност МСБ (Најзначајнији бит) и веома су важне када је у питању померање потписаних целих бројева. Разлог зашто се МСБ користи као пунило је да задржимо знак броја који се помера. Хајде да погледамо исти пример, осим што ћемо га направити негативним.

```c
11111111111111111111111111111000 //-8
>>
2

=

11111111111111111111111111111110 //-2
```

Очигледно, ово се понаша тачно исто као и претходни пример, осим што су леви битови коришћени за пунило јединицама; што доказује да је пунило за право аритметичко померање вредност МСБ.

### Лево померање

Ово је тачно обрнуто од оператора правог аритметичког померања. Он помера све битове у броју налево x пута. Хајде да погледамо пример.

```c
00000000000000000000000000001000  //8
<<
2

=

00000000000000000000000000100000 //32
```

Једина разлика између левог и десног аритметичког померања (осим смера померања) би било начин на који се обрађује пунило. Са десним аритметичким померањем, пунило је вредност МСБ (најзначајнији бит), али са левим аритметичким померањем вредност је само 0. Ово је зато што нема релевантних информација као што је знак броја који треба пратити.

```c
11111111111111111111111111111000 //-8
<<
2

=

11111111111111111111111111100000 //-32
```

Видите? Иако је пунило увек 0, знак броја је и даље сачуван. Једино на шта заиста треба обратити пажњу је померање превише. Ако померите позитиван број премаљу највећем могућем броју, постаће негативан, и обрнуто са негативним вредностима (крајње ћете стигнути до 0).

#### Логичка померања

##### Десно померање

Ово је обрнуто од аритметичког левог померања. Најбољи начин да се опише био би хибрид између оба аритметичка померања. Погледајмо како то функционише у пракси!

```c
00000000000000000000000000001000  //8
>>>
2

=

00000000000000000000000000000010 //2
```

Битови у броју 8 померени су 2 пута управо. Па како је ово било различито од аритметичког десног померања? Одговор је пунило. С аритметичким десним померањем, пунило је вредност МСБ-а, али са логичким десним померањем пунило је само 0 (као и са аритметичким левим померањем). Ово значи да неће задржати број знака, и наш резултат ће увек бити позитиван. Да бисмо то доказали, померићемо негативан број!

```c
11111111111111111111111111111000 //-8
>>>
2

=

00111111111111111111111111111110 //1073741822
```

То доказује да нећемо добити негативне вредности док користимо логичко десно померање!

##### Лево померање

Не постоји логичко лево померање, јер би радио тачно исто као и аритметичко лево померање. Само сам ово додала како би избегла било какву забуну и да бих држала одељак уравнотежен.

