---
title: "Direktfenster | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ImmediateWindow"
helpviewer_keywords: 
  - "Ausdrucksauswertung zur Entwurfszeit"
  - "Direktfenster"
  - "Ausnahmebenachrichtigungen (erste Chance)"
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Direktfenster
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Das Fenster **Direkt** wird zum Debuggen und Auswerten von Ausdrücken, Ausführen von Anweisungen, Drucken von Variablenwerten usw. verwendet.  Er ermöglicht die Eingabe von Ausdrücken, die von der Entwicklungssprache während des Debuggens ausgewertet oder ausgeführt werden sollen.  Um das Fenster **Direkt** anzuzeigen, öffnen Sie ein Projekt zur Bearbeitung und wählen dann im Menü **Debuggen** zunächst **Fenster** und dann **Direkt** aus, oder Sie drücken STRG\+ALT\+I.  
  
 Sie können in diesem Fenster einzelne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\-Befehle ausgeben.  Zu den verfügbaren Befehlen gehört `EvaluateStatement`. Damit können Variablen Werte zugewiesen werden.  Im Fenster **Direkt** wird außerdem IntelliSense unterstützt.  
  
## Anzeigen der Werte von Variablen  
 Dieses Fenster kann besonders beim Debuggen einer Anwendung von Nutzen sein.  Um beispielsweise den Wert der Variablen `varA` zu überprüfen, können Sie den [Befehl "Drucken"](../../ide/reference/print-command.md) verwenden:  
  
```  
>Debug.Print varA  
```  
  
 Das Fragezeichen \(?\) ist ein Alias für `Debug.Print`, sodass dieser Befehl auch wie folgt eingegeben werden kann:  
  
```  
>? varA  
```  
  
 Beide Versionen dieses Befehls geben den Wert der Variablen `varA` zurück.  
  
> [!NOTE]
>  Wenn Sie einen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\-Befehl im Fenster **Direkt** angeben, müssen Sie dem Befehl ein Größer\-als\-Zeichen \(\>\) voranstellen.  Wenn Sie mehrere Befehle eingeben möchten, wechseln Sie zum Fenster **Befehl**.  
  
## Ausdrucksauswertung zur Entwurfszeit  
 Sie können das Fenster **Direkt** verwenden, um eine Funktion oder Unterroutine zur Entwurfszeit auszuführen.  
  
#### So führen Sie eine Funktion zur Entwurfszeit aus  
  
1.  Kopieren Sie den folgenden Code in eine [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]\-Konsolenanwendung:  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MyFunction(5)  
        End Sub  
  
        Function MyFunction(ByVal input as Integer) As Integer  
            Return input * 2  
        End Function  
  
    End Module  
    ```  
  
2.  Wählen Sie im Menü **Debuggen** die Option **Fenster** aus, und klicken Sie dann auf **Direkt**.  
  
3.  Geben `?MyFunction(2)` im Fenster **Direkt** ein, und drücken Sie die EINGABETASTE.  
  
     Das Fenster **Direkt** führt `MyFunction` aus und zeigt `4` an.  
  
 Wenn die Funktion oder die Unterroutine einen Haltepunkt enthält, unterbricht [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Ausführung an der entsprechenden Stelle.  Sie können dann die Debuggerfenster verwenden, um den Programmzustand zu überprüfen.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Debuggen zur Entwurfszeit](../../debugger/walkthrough-debugging-at-design-time.md).  
  
 Die Ausdrucksauswertung zur Entwurfszeit ist nicht für Projekttypen verfügbar, die das Starten einer Ausführungsumgebung erfordern, z. B. [!INCLUDE[trprVSTOshort](../../ide/reference/includes/trprvstoshort_md.md)]\-Projekte, Webprojekte, Projekte für intelligente Geräte und SQL\-Projekte.  
  
### Ausdrucksauswertung zur Entwurfszeit in Projektmappen mit mehreren Projekten  
 Beim Festlegen des Kontexts für die Ausdrucksauswertung zur Entwurfszeit verweist [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] auf das aktuell ausgewählte Projekt im Projektmappen\-Explorer.  Wenn im Projektmappen\-Explorer kein Projekt ausgewählt ist, versucht [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], die Funktion anhand des Startprojekts auszuwerten.  Wenn die Funktion im aktuellen Kontext nicht ausgewertet werden kann, wird eine Fehlermeldung angezeigt.  Wenn Sie versuchen, eine Funktion in einem Projekt auszuwerten, das nicht das Startprojekt für die Projektmappe ist, und eine Fehlermeldung angezeigt wird, wählen Sie das Projekt im Projektmappen\-Explorer aus, und wiederholen Sie die Auswertung.  
  
## Eingeben von Befehlen  
 Sie müssen das Größer\-als\-Zeichen \(\>\) eingeben, wenn Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\-Befehle im Fenster **Direkt** angeben.  Verwenden Sie die NACH\-OBEN\- und NACH UNTEN\-TASTEN, um einen Bildlauf durch bereits ausgegebene Befehle durchzuführen.  
  
|Aufgabe|Lösung|Beispiel|  
|-------------|------------|--------------|  
|Auswerten eines Ausdrucks.|Stellen Sie dem Ausdruck ein Fragezeichen \(?\) voran.|`? a+b`|  
|Vorübergehendes Wechseln vom Direktmodus in den Befehlsmodus \(zum Ausführen eines einzelnen Befehls\).|Geben Sie den Befehl ein, und stellen Sie ihm ein Größer\-als\-Zeichen \(\>\) voran.|`>alias`|  
|Wechseln Sie zum Befehlsfenster.|Geben Sie im Fenster `cmd` ein, und stellen Sie dem Befehl ein Größer\-als\-Zeichen \(\>\) voran.|`>cmd`|  
|Wechseln Sie wieder zum Direktfenster.|Geben Sie in das Fenster `immed` ohne das Größer\-als\-Zeichen \(\>\) ein.|`immed`|  
  
## Markierungsmodus  
 Wenn Sie im Fenster **Direkt** auf eine zuvor ausgegebene Zeile klicken, schalten Sie automatisch in den Markierungsmodus um.  Auf diese Weise können Sie den Text vorheriger Befehle wie in einem beliebigen anderen Text\-Editor markieren, bearbeiten, kopieren und in die aktuelle Zeile einfügen.  
  
## Gleichheitszeichen \(\=\)  
 Abhängig vom Fenster, das zur Eingabe des `EvaluateStatement`\-Befehls verwendet wird, wird ein Gleichheitszeichen \(\=\) als Vergleichsoperator oder als Zuweisungsoperator interpretiert.  
  
 Im Fenster **Direkt** wird ein Gleichheitszeichen \(\=\) als Zuweisungsoperator interpretiert.  Daher wird mit dem Befehl  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 der Variablen `varA` der Wert von Variable `varB` zugewiesen.  
  
 Im Fenster **Befehl** wird ein Gleichheitszeichen \(\=\) hingegen als Vergleichsoperator interpretiert.  Sie können keine Zuweisungsvorgänge im Fenster **Befehl** ausführen.  Wenn die Werte der Variablen `varA` und `varB` beispielsweise unterschiedlich sind, gibt der Befehl  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 den Wert `False` zurück.  
  
## Ausnahmebenachrichtigungen \(erste Chance\)  
 Bei einigen Einstellungskonfigurationen werden Ausnahmebenachrichtigungen \(erste Chance\) im Fenster **Direkt** angezeigt.  
  
#### So blenden Sie Ausnahmebenachrichtigungen \(erste Chance\) im Direktfenster ein und aus  
  
1.  Klicken Sie im Menü **Ansicht** auf **Weitere Fenster** und dann auf **Ausgabe**.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Textbereich des **Ausgabefensters**, und aktivieren bzw. deaktivieren Sie die Option **Ausnahmemeldungen**.  
  
## Siehe auch  
 [Navigieren im Code mit dem Debugger](../../debugger/navigating-through-code-with-the-debugger.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Debuggen in Visual Studio](../../debugger/debugging-in-visual-studio.md)   
 [Debugger – Grundlagen](../../debugger/debugger-basics.md)   
 [Exemplarische Vorgehensweise: Debuggen zur Entwurfszeit](../../debugger/walkthrough-debugging-at-design-time.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)   
 [Verwenden von regulären Ausdrücken in Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)