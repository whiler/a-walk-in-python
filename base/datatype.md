## 数据类型 ##
数据类型是编程的基石，如同汉语的实词一样。
Python 的基础数据类型有 _None_ 、_整数（int）_ 、_实数（float）_、_布尔值（bool）_、_字符串（str）_，和由基础数据类型组合构成的 _集合（set）_、_元组（tuple）_、_列表（list）_ 和 _字典（dict）_ 。

### None ###
一无所有，但是还是有意义。
如同数学中的 _0_ 一样，表示没有任何值，但是它仍然有意义。
一般用于判断是否是 _None_ 。

例子：

```
nothing = None
```

### 整数 ###
和数学中的整数一样，Python 中的整数可以进行一切数学运算。

例子：

> 小明今年 10 岁，表弟小黑的年龄是小明的一半。
> 请问，小明 20 岁的时候，小黑多少岁？

```
xiaoming = 10
xiaohei = xiaoming / 2
xiaoming = 20
```

### 实数 ###
数学中的实数在计算机领域叫做浮点数（float），Python 中的实数同样可以进行一切数学运算。

例子：

> 每天进步一点点，一年进步了多少？
> $ 1.001^{365} = 1.4402513134295205 $

```
forward = 0.001
increase = 1.0 + forward
days = 365
total_increase = pow(increase, days)
```

### 布尔值 ###
只有 _真（True）_、_假（False）_ 两个值，一般用于判断真假。

例子：

> 你爱不爱我？

```
loveme = True
```


### 字符串 ###
Python 中，用单引号 _'_ 或者双引号 _"_ 或者三个双引号 _"""_ 引用起来的字符就是字符串。
字符串可以进行拼接、替换、拆分等操作。

例如：

> 西风烈，
> 长空雁叫霜晨月。
> 霜晨月，
> 马蹄声碎，喇叭声咽。
> 雄关漫道真如铁，
> 而今迈步从头越。
> 从头越，
> 苍山如海，残阳如血。

```
poem = '西风烈，长空雁叫霜晨月。霜晨月，马蹄声碎，喇叭声咽。雄关漫道真如铁，而今迈步从头越。从头越，苍山如海，残阳如血。'
poem = "西风烈，长空雁叫霜晨月。霜晨月，马蹄声碎，喇叭声咽。雄关漫道真如铁，而今迈步从头越。从头越，苍山如海，残阳如血。"
poem = """
西风烈，
长空雁叫霜晨月。
霜晨月，
马蹄声碎，喇叭声咽。
雄关漫道真如铁，
而今迈步从头越。
从头越，
苍山如海，残阳如血。
"""
poem = '西风烈，长空雁叫霜晨月。' + '霜晨月，马蹄声碎，喇叭声咽。' + '雄关漫道真如铁，而今迈步从头越。' + '从头越，苍山如海，残阳如血。'
```

为了打字时少按两次 shift 键，一般用单引号表示字符串。


### 集合 ###
概念和数学中的集合一致，计算方法和数学中一样，计算交集、并集等。

例如：

> 辛德勒和斯特恩打印了一张工人的名单，上面的人都不会被送往奥斯维辛。

```
schindlerjuden = {'Osias.Rubin', 'Jakob.Silberstein', 'Henryk.Heilmann', 'Chiel.Kohane', 'Menasche.Mindelgrun', 'Szymon.Mowschowitz', 'Bernard.Ingber', 'Max.Vogelhut', 'Zygmunt.Muller', 'Felix.Kaminski', 'Abraham.Schlesinger', 'Paul.Heller', 'Dawid.Urbach', 'Josek.Niemiec', 'Iszak.Hauben', 'Stefan.Gold', 'Moritz.Braun', 'Ludwig.Feigenbaum', 'Hersch.Pelzmann', 'Chana.Wachsberger', 'Rachmiel.Seidenfeuer', 'Helene.Geminder', 'Chaim.Selinger', 'Max.Silberstein', 'Chaim.Weiss', 'Moses.Schlesinger', 'Awadie.Kollender', 'Siegmund.Schonherz', 'Nachim.Wasserlauf', 'jakob.Perlmann', 'Laura.Stiel', 'Salo.Kukurutz', 'Benjamin.Gross', 'Erwin.Davidowitsch', 'Maurycy.Finder', 'Sara Estera.Wortszmann', 'Nachum.Monderer', 'Mieczyslaw.Garde', 'Josef.Scharf', 'Leib.Hudes', 'Ludwig.Herz', 'Max.Mindelgrun', 'Estera.Rosen', 'Felicia.Nadel', 'Debora.Lipschutz', 'Adolf.Grunhaut', 'Israel.Schneider', 'Marek.Konigl', 'Chaskel.Eckstein', 'Alexander.Mermelstein', 'Alexander.Adler', 'Alfred.Stelzer', 'Abraham.Sommer', 'Eli.Dubnikow', 'Kopel.Schulkind', 'Felicia.Blawat', 'Wiktor.Lezerkiewicz', 'Naftali.Baum', 'Jerzy.Gross', 'Moritz.Ettinger', 'Eliasz.Barth', 'Zygmunt.Hecht', 'Leib.Seewald', 'Beer.Rottenberg', 'Aron.Belbwerth', 'Eliasz.Luftig', 'Salomon.Urbach', 'Josef.Mozak', 'Asria.Lowi', 'Henryk.Gutherz', 'Szymon.Weingarten', 'Norbert.Bumfuhrer', 'Rena.Ring', 'Halina.Wohlfeiler', 'Estera.Pinkas', 'Artur.Juttla', 'Hirsch.Raber', 'Dawid.Scher', 'Gustawa.Gronner', 'Juliusz.Rosenberg', 'Salomon.Susskind', 'Szulam.Szlamowicz', 'Nuchym.Marlakow', 'Erich.Offner', 'Jakob.Feigenbaum', 'Rubin.Schadel', 'Abraham.Matuschak', 'Josef.Sterngast', 'Irena.Neumann', 'Aron.Klingenholz', 'Anna.Lermer', 'Herz.Hirschberg', 'Celina.Lampel', 'Estera.Friedmann', 'Henryka.Offmann', 'Natalia.Lewinska', 'Ruth.Lowenstein', 'Adolf.Elsner', 'Samuel.Krug', 'Wigdor.Dortheimer', 'Nysel.Stejman', 'Bella.Schonthal', 'Josef.Brayntich', 'Juda.Richter', 'Moszek.Knobler', 'Tauba.Kurz', 'Pinkus.Friedmann', 'Leib.Salpeter', 'Hermann.Loffler', 'Moniek.Susskind', 'Elzbieta.Rittermann', 'Abraham.Lermer', 'Naftali.Weil', 'Chaja.Wohlfeiler', 'Josef.Abusch', 'Jakob.Sussman', 'Adolf.Sussman', 'Paul.Schwarz', 'Jakob.Kremsdorf', 'Feiwel.Haar', 'Feiga Raza.Karp', 'Albert.Rosenfried', 'Natan.Bratkiewicz', 'Jonas.Penner', 'Wilhelm.Grauer', 'Josef.Weinstock', 'Sala.Stern', 'Eidla.Gerner', 'Majer.Rosenblatt', 'Samuel.Klassner', 'Alter.Binder', 'Jerzy.Kessler', 'Samuel.Deutelbaum', 'Max.Zimmermann', 'Mojzesz.Schimmel', 'Salka.Tennenbaum', 'Louis.Van Emden', 'Lore.Geminder', 'Lazar.Selinger', 'Josef.Keil', 'Maurycy.Linkowski', 'Mendel.Pilzmacher', 'Abraham.Herschlag', 'Eda.Lis', 'Josef.Brandeis', 'Mendel.Immergluck', 'Chaim.Fleischmann', 'Szulim.Leser', 'Henryk.Blatt', 'Szymon.Hirschberg', 'Marianne.Rosner', 'Leopold.Melzer', 'Ignacy.Liebermann', 'Hirsch.Beer', 'Mieczyslaw.Ponner', 'Roger.Michaud', 'Sara.Klinger', 'Benzion.Florenz', 'Franciszka.Penner', 'Felicia.Feldstein', 'Hilde.Berger', 'Fela.Ratz', 'Wolf.Horowitz', 'Josef.Haliczer', 'Toni.Teitelbaum', 'Ruth.Schiffer', 'Syda.Getzler', 'Samuel.Hirschfeld', 'Basia.Borenstein', 'Salomon.Wendum', 'Markus.Blum', 'Jechiel.Weingarten', 'Zygmunt.Rittermann', 'Szymon.Krieger', 'Chaim.Szlamowicz', 'Leon.Grobler', 'Malwina.Schlafstein', 'Berta.Muller', 'Max.Lang', 'Anatol.Manksleid', 'Max.Piskorz', 'Henryk.Kinstlinger', 'Adela.Karmel/Poss', 'Szaja.Kaufmann', 'Szyja.Abramoczyk', 'Ferdynand.Trauring', 'Isak Josef.Katz', 'Abram.Glicenstein', 'Bronislawa.Zweig', 'Isak.Preiss', 'Jakob.Gross', 'Osker.Grob', 'Adlea.Strom', 'Oskar.Feil', 'Maria.Markia', 'Helena.None', 'Ignaz.Nusbaum', 'Hirsch.Danzig', 'Hirsch.Biedermann', 'Chaskel.Krieger', 'Fritz.Buchhalter', 'Hanka.Gruner', 'Iser.Minz', 'Samuel.Wiener', 'Leonie.Grunberg', 'Juliusz.Baum', 'Rubin.Mutzenmacher', 'Icek.Lewkowicz', 'Hirsch.Chewel', 'Mojzesz.Bottner', 'Mendel.Freitag', 'Emil.Reich', 'Anna.Tanzer', 'Rosa.Feldmann', 'Josef.Horn', 'Eliasz.Horn', 'Jzak.Schweber', 'Pola.Gerner', 'Moses.Kopyto', 'Leon.Leibler', 'Lola.Reismann', 'Feiwel.Kleinmann', 'Jakob.Kornblau', 'Karol.Gross', 'Maurycy.Markheim', 'Aron.Stein', 'Dawid.Lewi', 'Sara.Dembitzer', 'Etka.Liebgold', 'Adolar.Gutherz', 'Sabina.Grunspan', 'Salomon.Pietrkowski', 'Estera.Schweizer', 'Jakob.Perlmann', 'Karola.Blumenkranz', 'Dawid.Lederer', 'Ezriel.Putter', 'Jakob.Oestreicher', 'Rosalia.Wohlfeiler', 'Stefania.Frisch', 'Jakob.Bierer', 'Moses.Federgrun', 'Siegfried.Gluckmann', 'Leontyna.Stern', 'Josek.Leichter', 'Emanuel.Taube', 'Jacob.Pudlowski', 'Adolf.Brenner', 'Menachem.Weiss', 'Leib.Teitelbaum', 'Izak.Kirschenbaum', 'Simon.Jereth', 'Chaim.Drisin', 'Rosa.Freilich', 'Salomon.Jachzel', 'Anna.Reich', 'Anschel.Freimann', 'Pinkus.Weinschelbaum', 'Abraham.Bankier', 'Abraham.Przeboznik', 'Valeria.Begleiter', 'Mendel.Blecheisen', 'Otto.Hansel', 'Heinrich.Lampel', 'Max.Biedermann', 'Leon.Bittersfeld', 'Syda.Selinger', 'Selman.Szydle', 'Josek.Lewin', 'Dawid.Lejzon', 'Joachim.Kirschenbaum', 'Miriam.Grunberg', 'Moyzesz.Gleitmann', 'Markus.Grabowski', 'Hanka.Rosenberg', 'Estera.Kerner', 'David.Haar', 'Jakob.Langsam', 'Jakob.Buchsbaum', 'Aron.Szczapa', 'Emil.Gruner', 'Benjamin.Breslauer', 'Leopold.Gruss', 'Simon.Klinghofer', 'Gedalie.Gluckmann', 'Idel.Goldstein', 'Franciszka.Friedner', 'Alexander.Schubert', 'Nachum.Weinberger', 'Izak.Hudes', 'Peter.Becsi', 'Dawid.Neiger', 'Viktor.Boger', 'Ada.Friedner', 'Siegfried.Baruch', 'Dezso.Neumann', 'Hela.Brzeska', 'Jenta.Zwetschenstiel', 'Wladyslaw.Kahane', 'Chaim.Zuckermann', 'Josek.Berger', 'Josef.Feiner', 'Israel.Falk', 'Golda.Bernstein', 'Isak.Silber', 'Szymon.Grossmann', 'Leon.Stein', 'Marcel.Goldwasser', 'Alter.Beer', 'Dawid.Garde', 'Dawid.Zimmet', 'Tauba.Tilles', 'Giza.Breit', 'Salomon.Herschlag', 'Josef.Melzer', 'Rosalia.Turk', 'Dawid.Grunwald', 'Lea.Hendler', 'Meier.Eichental', 'Ignaz.Herszkowitz', 'Estera.Zuckermann', 'Kalman.Goldberg', 'Aron.Goldstein', 'Izrael.Domb', 'Szaja.Ryba', 'Leon.Reisman', 'Chaskiel.Chajkin', 'Hermann.Wildstein', 'Chaskel.Goldberger', 'Abraham.Schuhmacher', 'Stefan.Begleiter', 'Motio.Geller', 'Ewa.Ratz', 'Jacob.Haller', 'Rafael.Bram', 'Simche.Birnzweig', 'Henoch.Herzberg', 'Salomon.Gruner', 'Leo.Finkelstein', 'Anita.Lampel', 'Jetti.Zimmerspitz', 'Helena.Schonherz', 'Szymon.Rosen', 'Ewa.Perlmann', 'Siegmund.Roter', 'Siegmund.Rado', 'Dora.Rath', 'Chaim.Grubner', 'Leopold.Schreiber', 'Mendel.Reich', 'Jakob.Pemper', 'Izydor.Tennenbaum', 'Izrael.Perlmann', 'Anna.Borger', 'Josef.Ickowicz', 'Fela.Zucker', 'Moses.Buchen', 'Simon.Pechner', 'Charlotte.Brandsilber', 'Jakob.Konig', 'Zew.Schanz', 'Anna.Hirsch', 'Josef.Kellner', 'Michael.Miedziuch', 'Jonas.Dresner', 'Natan.Brauer', 'Rosa.Ferber', 'Emanuel.Abzug', 'Perla.Leser', 'Moses.Gotinger', 'Ruth.Kohn', 'Moszek.Bejski', 'Eugenia.Finder', 'Chaim.Planzer', 'Erwin.Waldapfel', 'Fritz.Franken', 'Leon.Friedmann', 'Kiwa.Eisen', 'Josef Hilel.Borenstein', 'Natan.Stern', 'Leo.Knobloch', 'Leib.Lamensdorf', 'Abraham.Hirsch', 'Salomon.Grunfeld', 'Elias.Teitelbaum', 'Meier.Gartner', 'Fritz.Hartog', 'Maximilian.Kessler', 'Chaim.Salem', 'Helena.Rosner', 'Hersz.Jakubowski', 'Marta.Dressler', 'Rosalia.Presser', 'Eugenia.Ringelblum', 'Szymon.Tennenbaum', 'Tilla.Markin', 'Leib.Grycman', 'Leib.Frermann', 'Jerzy.Sternberg', 'Hermann.Gottselig', 'Dawid.Nadel', 'Leizor.Freitag', 'Maurycy.Pufeles', 'Adolf.Weinberger', 'Salomoa.Goldberg', 'Salomea.Schwarzmann', 'Moses.Apfel', 'Natan.Pelzmann', 'Samuel.Ehrlich', 'Chaja.Dresner', 'Moses.Schuldiener', 'Israel.Ferber', 'Horst.Wohlgemut', 'Natan.Kollmann', 'Nysen.Barth', 'Kalman.Obstler', 'Moszek.Bres', 'Sander.Folcusz', 'Michal.Ettinger', 'Elsa.Zimmerspitz', 'Rozalie.Klipstein', 'Chaim.Fertig', 'Dora.Perlberger', 'Halina.Brunnengraber', 'Moyzesz.Anglister', 'Pejsach.Figowicz', 'Eugenia.Wohlfeiler', 'Bronislawa.Presser', 'Michal.Essig', 'Maria.Penner', 'Rescha.Steinaaus', 'Jeremiasz.Kirschenbaum', 'Adolf.Frankel', 'Frania.Bielfeld', 'Meta.Schein', 'Hannelore.Wolf', 'Chaim.Berger', 'Perla.Mandel', 'Alfred.Herrmann', 'Danata.Dresner', 'Dawid.Fuchs', 'Henryk.Ettinger', 'Lola.Turk', 'Juda.Dresner', 'Juda.Katz', 'Moses.Turner', 'Feiwel.Wichter', 'Matilde Dr..Low', 'Ludwig.Elsner', 'Salomon.Reisfeld', 'Jakob.Leser', 'Toni.Schmidt', 'Moses.Lewkowicz', 'Sara.Horowitz', 'Otto.Goldberg', 'Wilhelm.Nachhauser', 'Pola.Ickowicz', 'Majer.Berger', 'Baruch.Posner', 'Markus.Weinberger', 'Aczer.Blatt', 'Eugenia.Friedmann', 'Cecilia.Zoldan', 'Ewa.Susskind', 'Klara.Sternberg', 'Mendel.Schweber', 'Stefania.Schonherz', 'Georg.Eisenberg', 'Henryk.Panzer', 'Moyzesz.Essig', 'Gabor.Holasz', 'Selig.Felsenstein', 'Salo.Allerhand', 'Paulina.Grossbard', 'Edmund.Korn', 'Ignacy.Grunfeld', 'Markus.Broder', 'Rafael.Steininger', 'Isak.Herz', 'Josef.Behrenhaut', 'Moses.Muller', 'Carmen.Weitmann', 'Szulim.Hollander', 'Frania.Presser', 'Doba.Nadel', 'Szaja.Koscher', 'Ruth.Steinhardt', 'Israel.Hirschhorn', 'Moritz.Reichgott', 'Rachela.Bugajer', 'Steffa.Offmann', 'Henryk.Opoczynska', 'Peretz.Selinger', 'Celina.Karp', 'Leopold.Luftig', 'Dawid.Herz', 'Sara Estera.Wahl', 'Szulim.Gorywocki', 'Bernard.Horowitz', 'Samuel.Kopec', 'Hersz.Blumenfrucht', 'Harry.Schnapp', 'Jakob.Haubenstock', 'Jakob.Tilles', 'Chana.Henig', 'Josef.Gutherz', 'Mendel.Lederer', 'Aron.Landschaft', 'Eugen.Klein', 'Chaim.Jakubowicz', 'Salomon.Feiler', 'Rita.Safier', 'Chaskiel.Ankier', 'Markus.Seifmann', 'Albert.Stillmann', 'Pesia.Lejzon', 'Kurt.Jakubowicz', 'Samuel.Baral', 'Friedrich.Beck', 'Cypora.Gross', 'Jadwiga.Rittermann', 'Wolf.Ratz', 'Izak.Hecht', 'Markus.Scheidlinger', 'Helga.Hirsch', 'Bella.Schwarzmann', 'Josef.Kraus', 'Mejzesz.Puntierer', 'Bernard.Presser', 'Chaim.Sperber', 'Josef.Kuchler', 'Paulina.Nessel', 'Schachne.Horowitz', 'Isidor.Eule', 'Alecksander.Muhlrad', 'Moses.Wahrhaft', 'Icek.Blum', 'Willy.Schlichting', 'Adolf.Borger', 'Rudolf.Friedmann', 'Regina.Semmel', 'Arje.Ferber', 'Rafal.Morgenbesser', 'Izak.Baldinger', 'Majer.Dreiblatt', 'Leopold.Degen', 'Mozes.Blum', 'Wladyslaw.Rath', 'Gisela.Appel', 'Chaim.Ptasznik', 'Mina.Feingold', 'Wilhelm.Rosner', 'Jetti.Zuckermann', 'Tibor.Bolaczy', 'Sofia.Buchsbaum', 'Viktor.Reif', 'Jaros.Stark', 'Abram.Klinburt', 'Anna.Geller', 'Naftali.Szlamowicz', 'Hersch.Mandel', 'Fryderyk.Appel', 'Josef.Ameizen', 'Naftali.Hudes', 'Mieczyslaw.Pempar', 'Teodor.Dembtizer', 'Paula.Kleinmann', 'Blima.Sichermann', 'Rela.Burstiner', 'Dawid.Hornung', 'Rachela.Hollander', 'Ignacy.Haber', 'Berek.Semmel', 'Moses.Goldmann', 'Otto.Schonfeld', 'Hirsch.Krischer', 'Hermann.Blechmann', 'Jerzy.Scheck', 'Dawid.Zalcberg', 'Rachela.Ast', 'Dawid.Weinzohelbaum', 'Jetti.Bronner', 'Abe.Rawet', 'Farkcas.Perlmutter', 'Erna.Eisen', 'Josef.Fried', 'Mira.Rosen', 'Aszer Edward.Spira', 'Josek.Ryba', 'Fiszel.Ejbuczyc', 'Wigdor.Roth', 'Marsk.Bossak', 'Wolf.Senft', 'Adolf.Kleinmann', 'Ferdinand.Hartmann', 'Eugen.Keller', 'Adolf.Blumenkranz', 'Josef.Bauer', 'Helena.Barth', 'Julius.Weiss', 'Fischel.Freiholf', 'Adam.Morgenbesser', 'Rudolf.Brechner', 'Jakob.Blaufelder', 'Fradel.Kiwetz', 'Olga.Opoczynska', 'Ida.Dawidowicz', 'Eleonara.Feuereisen', 'Mina.Neumann', 'Chaim.Hilfstein', 'Zenon.Szenwic', 'Szmul.Salzberg', 'Efroim.Fuhrmann', 'Sara.Rosenberg', 'Aron.Goldschmied', 'Siegfried.Saborsky', 'Richard.Nussbaum', 'Ruth.Katz', 'Isak.Zuckermann', 'Natan.Lewkowicz', 'Moses.Lejzon', 'Abraham.Joachimsman', 'Maurycy.Liebermann', 'Kalman.Meisels', 'Fela.Flinder', 'jakub.Rottmann', 'Hirsch.Silberstein', 'Chaim.Grungras', 'Cecilia.Pariser', 'Henryk.Glassner', 'Bronislaw.Friedmann', 'Artur.Rabner', 'Abraham.Auerbach', 'Szyja.Eichenholz', 'Sara.Heilmann', 'Zacharjasz.Kellner', 'Estera.Hudes', 'Dawid.Senftmann', 'Wolf.Elefant', 'Sara.Peller', 'Sydonia.Sternlicht', 'Jakub.Eisland', 'Josef.Rumpler', 'Moses.Perlmann', 'Jakob.Blammer', 'Wilhelm.Feiner', 'Cypera.Goldstein', 'Richard.Segal', 'Joachim.Dressler', 'Szmul.Brambrot', 'Jakob.Ewensohn', 'Stefan.Goldstein', 'Moses.Horowitz', 'Jankiel Dawid.Salzberg', 'Ludmila.Pfeffeberg', 'Dawid.Dringer', 'Markus.Wulkan', 'Henryk.Wohlfeiler', 'Jakob.Sternberg', 'Jakob.Gewelbe', 'Abraham.Grun', 'Szyfra.Durst', 'Cecilia.Wasserteil', 'Lemel.Geiger', 'Chaim.Korber', 'Mira.Garde', 'Adela.Sterngast', 'Felicia.Friedmann', 'Moses.Klinstlinger', 'Erna.Rothberg', 'Adolf.Guttmann', 'Leib.Gerstner', 'Lola.Banach', 'Bernhard.Goldstein', 'Saal.Oppenheim', 'Kuba.Beck', 'Abraham.Jachzel', 'Berta.Aftergut', 'Leopold.Schlesinger', 'Herman Natan.Feldmann', 'Stefan.Luftig', 'Hersz.Pomeranz', 'Wolf.Feldstein', 'Miriam.Hilfstein', 'Chana.Kief', 'Ernestine.Ginter', 'Sulamith.Sauerbrunn', 'Markus.Spiegel', 'Fela.Geminder', 'Majer.Metzendorf', 'Paula.Leder', 'Cedale.Vogel', 'Zdenek.Hoffmann', 'Osias.Weiser', 'Natan.Kruger', 'Moritz.Sperling', 'Pinkus.Chiel', 'Anna.Lichtig', 'Wolf.Wein', 'Bernard.Hillmann', 'Heinz.Jospe', 'Lola.Feldmann', 'Julek.Ordynansa', 'Hirsch.Ehrlich', 'Emil.Inslicht', 'Leon.Kaufmann', 'Alexander.Bieberstein', 'Jerzy.Reich', 'Abe.Ptasznik', 'Rozalia.Kornhauser', 'Ignazy.Birnback', 'Genia.Gams', 'Samuel.Schindel', 'Hersch.Goldkern', 'Balka.Weinstock', 'Maurycy.Gangel', 'Henryka.Lis', 'Jakob.Jakubowicz', 'Adam.Muller', 'Ryszard.Rechen', 'Hermann.Lewkowicz', 'Stefan.Pemper', 'Jakob.Laus', 'Leopold.Ring', 'Paul.Stagel', 'Gabriela.Katz', 'Roman.Wohlfeiler', 'Gisela.Nessel', 'Szymon.Seliger', 'Szya.Kestenberg', 'Henryk.Kammermann', 'Otto.Gross', 'Eduard.Danziger', 'Edward.Heuberger', 'Wladyslaw.Berger', 'Salomon.Perl', 'Dawid.Sauerbrunn', 'Franciszok.Rozeriszok', 'Aron.Eisenstein', 'Cecilia.Frey', 'Izak.Fluss', 'Izrael.Kupferberg', 'Bernard.Goldberg', 'Henryk.Klugmann', 'Abraham.Grunberg', 'Henryk.Blasenstein', 'Chaim.Beer', 'Josef.Milgrom', 'Desider.Kahan', 'Alfred.Schonfeld', 'Baruch.Wachholder', 'Abraham.Putter', 'Estera.Herzog', 'Jarum.Kinstlinger', 'Alexander.Goldwasser', 'Mala.Mandelbaum', 'Saul.Gruner', 'Soltan.Kellner', 'Chana.Lejzon', 'Aron.Feilgut', 'Srul.Weinzier', 'Cyla.Katolik', 'Chaja.Wulkan', 'Izrael Berek.Bejski', 'Maksymilian.Taube', 'Jakob.Lewertow', 'Abraham.Gross', 'Irena.Scheck', 'Henryk.Goudstikker', 'Szulim.Vogelmann', 'Bernard.Feuermann', 'Israel.Makowski', 'Aszer Edward.Stern', 'Renata.Kuzmer/Lewkowicz', 'Moses.Sussermann', 'Hanka.Ring', 'Ascher.Jasse', 'Jerzy.Spira', 'Hermann.Katz', 'Miklosz.Nadler', 'Edward.Hilfstein', 'Chaja.Jereth', 'Augusta.Gutherz', 'Izrael.Goldfarb', 'Abram.Wisniak', 'Szulim.Scheinok', 'Abraham.Balicki', 'Abraham.Grossmann', 'Efroim.Bleiweig', 'Herta.Nussbaum', 'Franciszka.Spira', 'Hans.Nebel', 'Alfred.Pemper', 'Hersch.Licht', 'Anna.Schneeweiss', 'Leon.Frankel', 'Hersz.Flinkt', 'Estera.Korn', 'Sara.Grajower', 'Ignacy.Kurz', 'Julius.Hirschel', 'Arnold.Ringelblum', 'Abraham.Kormann', 'Dusia.Linzer', 'Salomon.Frankel', 'Roma.Horowitz', 'Georg.Schwelb', 'Czeslawa.Kraus', 'Wilhelm.Taubler', 'Leopold.None', 'Jakob.Davidson', 'Gustawa.Ruckel', 'Irena.Relich', 'Gustawa.Fertig', 'Szymon.Starzycki', 'Ryfka.Schenker', 'Jakob.Low', 'Markus.Dienstag', 'Moses.Frei', 'Sabina.Grunwald', 'Leon.Lindenberger', 'Helena.Hirsch', 'Henryk.Turner', 'Zysze.Low', 'Samuel.Sawicki', 'Samuel.Frisch', 'Josef.Hornung', 'Anna.Konigsberg', 'Henryk.Kornfeld', 'Sofia.Haubenstock', 'Erich.Glinski', 'Szymon.Strenger', 'Irena.Garde', 'Frieda.Frankel', 'Roman.Kukurutz', 'Salomon.Hartmann', 'Wilhelm.Kranz', 'Sara.Orbach', 'Josef.Chlebowski', 'Siegmar.Seif', 'Rosa.Glockenberg', 'Izak Szyja.Karp', 'Robert.Pollak', 'Susi.Dressler', 'Bluma.Reicher', 'Gunther.Singer', 'Siegmund.Neumann', 'Zalel.Jazowski', 'Adolf.Radziwiller', 'Dawid.Mond', 'Juda.Merkrebs', 'Selig.Kopec', 'Adela.Lowi', 'Ryszard.Lax', 'Cecilia.Katz', 'Sadek.Wilk', 'Lea.Herzog', 'David.Diktoriczyk', 'Josef.Stein', 'Josef.Gross', 'Max.Korzeo', 'Szloma.Pozniak', 'Szaja.Kleinberg', 'Efreim.Goldberg', 'Dawid.Hahn', 'Adam.Garde', 'Fischel.Beder', 'Szymon.Nadel', 'Moses.Rimmler', 'Bronislawa.Horowitz', 'Abraham.Reiss', 'Lobl.Friedner', 'Lazar.Feit', 'Jerzy.Brauner', 'Fischel.Roth', 'Izak.Landesdorfer', 'Hermina.Offmann', 'Helena.Dortheimer', 'Feiga.Seelenfreund', 'Chaim.Segal', 'Arnold.Goldberger', 'Hermann.Kornhauser', 'Hella.Schenierer', 'Ismar.Fischer', 'Helene.Landsberger', 'Ludwig.Kornfeld', 'Dawid.Altmann', 'Ignacy.Klinghofer', 'Szymon.Schein', 'Jgnaz.Eckstein', 'Sabina.Loffel', 'Jan.Liban', 'Yoniek.Chojna', 'Oskar.Schimmel', 'Josef.Sommer', 'Alfred.Nichthauser', 'Helena.Gruner', 'Anna.Duklauer', 'Chaim.Brotmann', 'Salomon.Lewi', 'Chaim.Perlmann', 'Majer.Korner', 'Sara.Danzig', 'Hanka.Schmidt', 'Hersch.Silberschlag', 'Samuel.Grobler', 'Polda.Hirschfeld', 'Szymon.Smolarz', 'Moses.Krebs', 'Israel.Rosenthal', 'Henja Malka.Bernstein', 'Moszek.Grossmann', 'Juliusz.Wiener', 'Berta.Tanzer', 'Adolf.Goldstein', 'Benjamin.Feingerson', 'Moses.Wasserteil', 'Samuel.Lichtig', 'Fanny Debora.Penner', 'Abraham.Feiler', 'Dora.Schwed', 'Helena.Friedmann', 'Samuel.Stimmler', 'Roman.Wachtel', 'Alexander.Schwarz', 'Rena.Ferber', 'Afdolf.Oberfeld', 'Ruchel.Horowitz', 'Jankiel.Kujawski', 'Moses.Goldberg', 'Wilhelm.Nussbaum', 'Berl.Weinstein', 'Ital.Lewkowicz', 'Marcel.Goldberg', 'Michael.Borger', 'Roman.Schreier', 'Alexander.Bialywlos', 'Jeremiasz.Mutzner', 'Adolf.Berger', 'Berisch.Goldberg', 'Isak.None', 'Izak.Izraelowicz', 'Efroim.Sperling', 'Bernard.Kleiner', 'Hersz.Freitag', 'Robert.Brock', 'Regina.Kaufmann', 'Rega.Peller', 'Henryk.Stern', 'Roman.Goldberger', 'Frajda.Szypiacka', 'Chaim.Malawer', 'Leopold.Fischgrund', 'Israel.Wiener', 'Moisze.Honigmann', 'Jankiel.Sloma', 'Majlech.Garfunkiel', 'Szaja.Rosenblum', 'Szaja.Handler', 'Isak.Schreiber', 'Ala.Kupferberg', 'Nina.Heublum', 'Markus.Kohn', 'Stella.Muller', 'Jakob.Armer', 'Markus.Birnfeld', 'Bella.Lehrer/Handler', 'Samuel.Beckman', 'Izak.Lebenstein', 'Daniel.Gross', 'Markus.Wandersmann', 'Bronia.Gunz/Sperling', 'Lola.Krumholz', 'Maks.Rosenzweig', 'Moses.Rechtschaffer', 'Michal Leib.Hellmann', 'Teodor.Perlberger', 'Alexander.Grunfeld', 'Jakob.Kleinmann', 'Henryk.Neufeld', 'Kalman.Reich', 'Heinz.Dressler', 'Elka.Berhang', 'Ferdinand.Massaryk', 'Stella.Israeli', 'Bernard.Kornhauser', 'Rosalia.Nussbaum', 'Selma.Gross', 'Felicia.Rosenbluth', 'Necha.Feigenbaum', 'Symcha.Weiss', 'Mirko.Koniowitsch', 'Abraham.Gruss', 'Lejbusz.Wachsberg', 'Monick.Weinstock', 'Baruch.Reisfeld', 'Berthold.Hornitzer', 'Baruch.Pomeranz', 'Schulim.Wachholder', 'Hania.Schlesinger', 'Halina.Horowitz', 'Max.Stemmer', 'Dawid.Ausubel', 'Moyzesz.Lederberger', 'Henryk.Brautmann', 'Leopold.Bronner', 'Regina.Schonthal', 'Josek.Freihof', 'Natan.Gurfinkel', 'Maria.Wiener', 'Salomon.Goldblatt', 'Hinde Debora.Goldmann', 'Maria.Haubenstock', 'Izak Dawid.Klipstein', 'Ella.Frisch', 'Sali.Hirschberg', 'Syda.Goldberg', 'Hermann.Forkus', 'Naftali.Glucksmann', 'Rataal.Rottenberg', 'Szaja.Lasser', 'Nelli.Brechnor', 'Stefania.Trauring', 'David.Flinkt', 'Rachela.Korn', 'Bronislawa.Sternlicht', 'Szlama.Meisels', 'Aron.Reismann', 'Dawid.Schlang', 'Juda.Birnbaum', 'Josef.Lipschutz', 'Gusta.Pelzmann', 'Jakob.Weingarten', 'Salomon.Goldberger', 'Maria.Mischel', 'Izydor.Horowitz', 'Roma.Nass', 'Sandor.Feuermann', 'Salomea.Liebermann', 'Markus.Lieser', 'Salomea.Urbach', 'Zygmunt.Immergluck', 'Meilech.Gurewicz', 'Dawid.Gottselig', 'max.Rosenkranz', 'Salomon.Salsam', 'Gisela.Srebrna', 'Josef.None', 'Baruch.Weismann', 'Cecilia.Brzeska', 'Helena.Kuhn', 'Szyja.Kern', 'Syda.Stiel', 'Teofila.Tauss', 'Meier.Kleiner', 'Lewi.Berlinerblau', 'Ester.Wadler', 'Jakob.Herszkowicz', 'Eliasz.Leinkram', 'Karol.Emmerich', 'Dawid.Jakubowicz', 'Abraham.Mahler', 'Natan.Spatz', 'Henoch.Nussbaum', 'Bella.Horowitz', 'Alexander.Goldmann', 'Krystyna.Wohlfeiler', 'Alexander.Entracht', 'Szmul.Cajg', 'Abraham.Stanger', 'Natan.Rosen', 'Perl.Holzmann', 'Erna.Schonherz', 'Leib.Lejzon', 'Josef.Jonas', 'Bernard.Eilberg', 'Chaim.Feinberg', 'Rena.Wohlfeiler', 'Bernard.Sperling', 'Jakob.Seftel', 'Pinkus.Eidner', 'Fiszel.Fried', 'Ignazy.Wohlfeiler', 'Jakob.Grunblum', 'Urysz.Bejski', 'Izak.Silberspitz', 'Rosa.Laufer', 'Ferdynand.Lewkowicz', 'Leon.Hirsch', 'Tauba.Manne'}
```


### 元组 ###
固定的组合，组合的顺序不能变，组合的元素也不能变。
元组用于对顺序要求严格的场景。

例如：

> 家族团聚，不能乱坐！

```
seats = ('爷爷', '奶奶', '大伯')
```

### 列表 ###
可变的组合，组合的顺序可变，组合的元素也可变。
列表可以进行添加、插入、移除操作。

例如，一个购物单：

```
shopping_list = ['牙膏', '薯片', '牛奶', '啤酒']
shopping_list.append('口香糖')
shopping_list.insert(0, '泡面')
shopping_list.remove('牛奶')
```

### 字典 ###
字典表示一种对应关系，和现实中的使用场景一致，用于快速查找。

例如：

```
dictionary = {'cat': '猫', 'temple': '寺庙'}
```


集合用花括号 _{}_ 包裹集合中的各个元素，元组用括号 _()_ ，列表用中括号 _[]_ 。

同样是用花括号 _{}_ 包裹各个元素的字典（dict），它的各个元素由用 _:_ 拼接的两部分组成，_:_ 前的部分是键（key）用于快速检索， _:_ 后是值（value）表示键对应的数据。


纸牌 _2_ , 在德州扑克中几乎是最小的牌，但是在斗地主的时候拿到会暗自高兴的。
同样的一张扑克牌 _2_ ，在不的玩法中的意义也不同。
在计算机中，数据的本质是二进制的 _0_ 和 _1_ 的组合，解释方式的不同产生了不同的数据类型和值。
二进制 _101111111000011_ 按照整数读取便得到 _24515_，若按照字符串读取便得到汉字 _“心_ ”。
