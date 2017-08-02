---
title: "Verwenden von IntelliSense | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.tools.intellisense"
helpviewer_keywords: 
  - "Wort vervollständigen"
  - "IntelliSense"
  - "IntelliSense [Visual Studio]"
  - "IntelliSense, Wort vervollständigen"
  - "IntelliSense, Beendigungsmodus"
  - "IntelliSense, Anpassen"
  - "IntelliSense, Member auflisten"
  - "IntelliSense, Parameterinfo"
  - "IntelliSense, Vorschlagsmodus"
  - "Member auflisten"
  - "Parameterinfo"
  - "Parameterinformationen"
  - "QuickInfo"
ms.assetid: 9fdb489b-8b46-4b92-9ccc-c8f8cc184081
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Verwenden von IntelliSense
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

IntelliSense ist der allgemeine Begriff für eine Reihe von Funktionen: Member auflisten, Parameterinfo, QuickInfo und Wort vervollständigen.  Mithilfe dieser Funktionen erfahren Sie mehr über den verwendeten Code, Sie können die eingegebenen Parameter verfolgen und mit wenigen Tastaturanschlägen Eigenschaften und Methoden zu Aufrufen hinzufügen.  
  
 Viele Aspekte von IntelliSense sind sprachspezifisch.  Weitere Informationen zu IntelliSense für verschiedene Sprachen finden Sie in den Themen, die unter "Siehe auch" aufgelistet sind.  
  
## Member auflisten  
 Eine Liste gültiger Member von einem Typ \(oder Namespace\) wird angezeigt, nachdem Sie ein Triggerzeichen eingegeben haben, beispielsweise einen Punkt \(`.`\) im verwalteten Code oder `::` in C\+\+.  Wenn Sie mit der Zeicheneingabe fortfahren, wird die Liste so gefiltert, dass sie nur die Member enthält, die mit diesen Zeichen beginnen.  
  
 Nachdem Sie ein Element ausgewählt haben, können Sie es in den Code einfügen, indem Sie die TAB\-TASTE drücken oder ein Leerzeichen eingeben.  Wenn Sie ein Element auswählen und einen Punkt eingeben, wird das Element gefolgt von dem Punkt angezeigt. Dadurch wird eine andere Memberliste aufgerufen.  Wenn Sie ein Element auswählen, bevor Sie es einfügen, erhalten Sie QuickInfos über das Element.  
  
 In der Memberliste stellt das Symbol auf der linken Seite den Membertyp dar, z. B. Namespace, Klasse, Funktion oder Variable.  Eine Liste der Symbole finden Sie unter [Symbole in der Klassenansicht und im Objektbrowser](../ide/class-view-and-object-browser-icons.md).  Die Liste kann ziemlich lang sein, und Sie können BILD\-AUF und BILD\-AB drücken, um nach oben oder unten zu navigieren.  
  
 ![Visual Studio, Member&#45;Liste](../ide/media/vs2015_intellisense.png "vs2015\_Intellisense")  
  
 Sie können die Funktion **Member auflisten** manuell aufrufen, indem Sie STRG\+J eingeben und auf **Bearbeiten \> IntelliSense \> Member auflisten** klicken, oder indem Sie auf die Schaltfläche **Member auflisten** auf der Symbolleiste des Editors klicken.  Wenn die Memberliste in einer Leerzeile oder außerhalb eines erkennbaren Gültigkeitsbereichs aktiviert wird, werden Symbole im globalen Namespace angezeigt.  
  
 Um die Auflistung der Member standardmäßig zu deaktivieren \(sodass sie nur mehr nach einem speziellem Aufruf angezeigt wird\), rufen Sie **Extras \> Optionen \> Alle Sprachen** auf, und deaktivieren Sie **Member automatisch auflisten**.  Wenn Sie die Auflistung der Member nur für eine bestimmte Sprache deaktivieren möchten, wechseln Sie zu den Einstellungen **Allgemein** für diese Sprache.  
  
 Sie können auch in den Vorschlagsmodus wechseln, in dem nur der von Ihnen eingegebene Text in den Code eingefügt wird.  Wenn Sie beispielsweise einen Bezeichner eingeben, der sich nicht in der Liste befindet, und dann die TAB\-TASTE drücken, ersetzt der Eintrag im Beendigungsmodus den typisierten Bezeichner.  Um zwischen Beendigungsmodus und Vorschlagsmodus zu wechseln, drücken Sie STRG\+ALT\+LEERTASTE, oder klicken Sie auf **Bearbeiten \> IntelliSense \> Beendigungsmodus umschalten**.  
  
## Parameterinfo  
 Die Parameterinfo liefert Informationen über die Anzahl, Namen und Typen der Parameter, die von einer Methode, einem attributgenerischen Typparameter \(in C\#\) oder einer Vorlage \(in C\+\+\) benötigt werden.  
  
 Der Parameter, den Sie beim Eingeben der Funktion als Nächstes angeben müssen, ist fett dargestellt.  Bei überladenen Funktionen können Sie die Pfeiltasten verwenden, um alternative Parameterinformationen für die Funktionsüberladungen anzuzeigen.  
  
 ![Parameterinfo](~/docs/ide/media/vs2015_param_info.png "VS2015\_param\_Info")  
  
 Wenn Sie Funktionen und Parameter mit XML\-Dokumentationskommentaren versehen, werden die Kommentare als Parameterinfo angezeigt.  Weitere Informationen finden Sie unter [Anzeigen von XML\-Codekommentaren](../ide/supplying-xml-code-comments.md).  
  
 Sie können die Parameterinfo manuell aufrufen, indem Sie auf **IntelliSense bearbeiten \> Parameterinfo** klicken und dann CTRL\+SHIFT\+SPACE eingeben, oder indem Sie auf die Schaltfläche **Parameterinfo** auf der Symbolleiste des Editors klicken.  
  
## QuickInfo  
 QuickInfo zeigt die vollständige Deklaration eines beliebigen Bezeichners im Code an.  
  
 ![Visual Studio&#45;QuickInfo](~/docs/ide/media/vs2015_quick_info.png "VS2015\_Quick\_info")  
  
 Wenn Sie einen Member im Feld **Member auflisten** auswählen, wird ebenfalls eine QuickInfo angezeigt.  
  
 ![Parameterinfo in einer C&#35;&#45;Codedatei](~/docs/ide/media/vs2015_paraminfo.png "VS2015\_ParamInfo")  
  
 Sie können die QuickInfo manuell aufrufen, indem Sie auf **Bearbeiten \> IntelliSense \> QuickInfo** klicken und dann STRG\+I eingeben, oder indem Sie auf die Schaltfläche **QuickInfo** auf der Symbolleiste des Editors klicken.  
  
 Wenn eine Funktion überladen ist, zeigt IntelliSense u. U. nicht für alle Formulare der überladenen Funktion Informationen an.  
  
 Sie können die QuickInfo in C\+\+ deaktivieren, indem Sie **Extras \> Optionen \> Text\-Editor \> C \> C\+\+ \> Erweitert \> Automatische QuickInfo** auf `falsch` setzen.  
  
## Wort vervollständigen  
 Die Option "Wort vervollständigen" ergänzt den Rest eines Variablen\-, Befehls\- oder Funktionsnamens, sobald Sie so viele Zeichen eingegeben haben, dass der Name eindeutig erkannt werden kann.  Sie können "Word vollständigen" aufrufen, indem Sie auf **Bearbeiten \> IntelliSense \> Wort vervollständigen** klicken und dann STRG\+LEERTASTE eingeben, oder indem Sie auf die Schaltfläche **Wort vervollständigen** auf der Symbolleiste des Editors klicken.  
  
## IntelliSense\-Optionen  
 IntelliSense\-Optionen sind standardmäßig aktiviert.  Um sie zu deaktivieren, klicken Sie auf **Extras \> Optionen \> Text\-Editor** und deaktivieren Sie **Parameterinformationen** oder **Member automatisch auflisten**, wenn Sie die Funktion "Member auflisten" nicht verwenden möchten.  
  
## Problembehandlung bei IntelliSense  
 In bestimmten Fällen kann es vorkommen, dass IntelliSense\-Optionen nicht wie erwartet funktionieren.  
  
 **Der Cursor befindet sich unter einem Codefehler.** Sie können IntelliSense möglicherweise nicht verwenden, wenn eine unvollständige Funktion oder ein anderer Fehler im Code über dem Cursor vorhanden ist, weil IntelliSense die Codeelemente eventuell nicht analysieren kann.  Sie können dieses Problem beheben, indem Sie den betreffenden Code auskommentieren.  
  
 **Der Cursor befindet sich in einem Codekommentar.** Sie können IntelliSense nicht verwenden, wenn sich der Cursor in einem Kommentar in Ihrer Quelldatei befindet.  
  
 **Der Cursor befindet sich in einem Zeichenfolgenliteral.** Sie können IntelliSense nicht verwenden, wenn sich der Cursor innerhalb der Anführungszeichen um ein Zeichenfolgenliteral befindet, wie im folgenden Beispiel dargestellt:  
  
```  
MessageBox( hWnd, "String literal|") )  
```  
  
 **Die automatischen Optionen sind deaktiviert.** Standardmäßig funktioniert IntelliSense automatisch, Sie können es jedoch deaktivieren.  Auch wenn die automatische Anweisungsvervollständigung deaktiviert ist, können Sie eine IntelliSense\-Funktion aufrufen.  
  
## Siehe auch  
 [Visual Basic\-spezifisches IntelliSense](../ide/visual-basic-specific-intellisense.md)   
 [Visual C\#\-IntelliSense](../ide/visual-csharp-intellisense.md)   
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [Anzeigen von XML\-Codekommentaren](../ide/supplying-xml-code-comments.md)