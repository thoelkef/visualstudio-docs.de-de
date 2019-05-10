---
title: Direktfenster | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e6bbbd4fa2ad051407ece3e05c1806c1231ef2e8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437121"
---
# <a name="immediate-window"></a>Direktfenster
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Das Fenster **Direkt** wird zum Debuggen und Auswerten von Ausdrücken, Ausführen von Anweisungen, Drucken von Variablenwerten usw. verwendet. Er ermöglicht die Eingabe von Ausdrücken, die von der Entwicklungssprache während des Debuggens ausgewertet oder ausgeführt werden sollen. Um das Fenster **Direkt** anzuzeigen, öffnen Sie ein Projekt zur Bearbeitung und wählen dann im Menü **Debuggen** zunächst **Fenster** und dann **Direkt** aus, oder drücken Sie STRG+ALT+I.  
  
 Sie können in diesem Fenster einzelne [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Befehle ausgeben. Zu den verfügbaren Befehlen gehört `EvaluateStatement`. Damit können Variablen Werte zugewiesen werden. Das Fenster **Direkt** unterstützt auch IntelliSense.  
  
## <a name="displaying-the-values-of-variables"></a>Anzeigen der Werte von Variablen  
 Dieses Fenster kann besonders beim Debuggen einer Anwendung von Nutzen sein. Um beispielsweise den Wert der Variablen `varA` zu überprüfen, können Sie den [Drucken-Befehl](../../ide/reference/print-command.md) verwenden:  
  
```  
>Debug.Print varA  
```  
  
 Das Fragezeichen (?) ist ein Alias für `Debug.Print`, sodass dieser Befehl auch wie folgt eingegeben werden kann:  
  
```  
>? varA  
```  
  
 Beide Versionen dieses Befehls geben den Wert der Variablen `varA` zurück.  
  
> [!NOTE]
> Wenn Sie einen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Befehl im Fenster **Direkt** angeben, müssen Sie dem Befehl ein Größer-als-Zeichen (>) voranstellen. Wechseln Sie zum Fenster **Befehl**, wenn Sie mehrere Befehle eingeben möchten.  
  
## <a name="design-time-expression-evaluation"></a>Ausdrucksauswertung zur Entwurfszeit  
 Sie können das Fenster **Direkt** verwenden, um eine Funktion oder Unterroutine zur Entwurfszeit auszuführen.  
  
#### <a name="to-execute-a-function-at-design-time"></a>So führen Sie eine Funktion zur Entwurfszeit aus  
  
1. Kopieren Sie den folgenden Code in eine [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]-Konsolenanwendung:  
  
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
  
2. Wählen Sie im Menü **Debuggen** die Option **Fenster** aus, und klicken Sie dann auf **Direkt**.  
  
3. Geben `?MyFunction(2)` im Fenster **Direkt** ein, und drücken Sie die EINGABETASTE.  
  
    Das Fenster **Direkt** führt `MyFunction` aus und zeigt `4` an.  
  
   Wenn die Funktion oder die Unterroutine einen Haltepunkt enthält, unterbricht [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] die Ausführung an der entsprechenden Stelle. Sie können dann die Debuggerfenster verwenden, um den Programmzustand zu überprüfen. Weitere Informationen finden Sie unter [Walkthrough: Debugging at Design Time (Exemplarische Vorgehensweise: Debuggen zur Entwurfszeit)](../../debugger/walkthrough-debugging-at-design-time.md).  
  
   Die Ausdrucksauswertung zur Entwurfszeit ist nicht für Projekttypen verfügbar, die das Starten einer Ausführungsumgebung erfordern, z. B. [!INCLUDE[trprVSTOshort](../../includes/trprvstoshort-md.md)]-Projekte, Webprojekte, Projekte für intelligente Geräte und SQL-Projekte.  
  
### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Ausdrucksauswertung zur Entwurfszeit in Projektmappen mit mehreren Projekten  
 Beim Festlegen des Kontexts für die Ausdrucksauswertung zur Entwurfszeit verweist [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] auf das aktuell ausgewählte Projekt im Projektmappen-Explorer. Wenn im Projektmappen-Explorer kein Projekt ausgewählt ist, versucht [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], die Funktion anhand des Startprojekts auszuwerten. Wenn die Funktion im aktuellen Kontext nicht ausgewertet werden kann, wird eine Fehlermeldung angezeigt. Wenn Sie versuchen, eine Funktion in einem Projekt auszuwerten, das nicht das Startprojekt für die Projektmappe ist, und eine Fehlermeldung angezeigt wird, wählen Sie das Projekt im Projektmappen-Explorer aus, und wiederholen Sie die Auswertung.  
  
## <a name="entering-commands"></a>Eingeben von Befehlen  
 Sie müssen das Größer-als-Zeichen (>) eingeben, wenn Sie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Befehle im Fenster **Direkt** angeben. Verwenden Sie die NACH-OBEN- und NACH UNTEN-TASTEN, um einen Bildlauf durch bereits ausgegebene Befehle durchzuführen.  
  
|Aufgabe|Lösung|Beispiel|  
|----------|--------------|-------------|  
|Auswerten eines Ausdrucks.|Stellen Sie dem Ausdruck ein Fragezeichen (?) voran.|`? a+b`|  
|Vorübergehendes Wechseln vom Direktmodus in den Befehlsmodus (zum Ausführen eines einzelnen Befehls).|Geben Sie den Befehl ein, und stellen Sie ihm ein Größer-als-Zeichen (>) voran.|`>alias`|  
|Wechseln Sie zum Befehlsfenster.|Geben Sie im Fenster `cmd` ein, und stellen Sie dem Befehl ein Größer-als-Zeichen (>) voran.|`>cmd`|  
|Wechseln Sie wieder zum Direktfenster.|Geben Sie in das Fenster `immed` ohne das Größer-als-Zeichen (>) ein.|`immed`|  
  
## <a name="mark-mode"></a>Markierungsmodus  
 Wenn Sie im Fenster **Direkt** auf eine zuvor ausgegebene Zeile klicken, schalten Sie automatisch in den Markierungsmodus um. Auf diese Weise können Sie den Text vorheriger Befehle wie in einem beliebigen anderen Text-Editor markieren, bearbeiten, kopieren und in die aktuelle Zeile einfügen.  
  
## <a name="the-equals--sign"></a>Gleichheitszeichen (=)  
 Abhängig vom Fenster, das zur Eingabe des `EvaluateStatement`-Befehls verwendet wird, wird ein Gleichheitszeichen (=) als Vergleichsoperator oder als Zuweisungsoperator interpretiert.  
  
 Im Fenster **Direkt** wird ein Gleichheitszeichen (=) als Zuweisungsoperator interpretiert. Daher wird mit dem Befehl  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 der Variablen `varA` der Wert von Variable `varB` zugewiesen.  
  
 Im Fenster **Befehl** wird ein Gleichheitszeichen (=) hingegen als Vergleichsoperator interpretiert. Sie können keine Zuweisungsvorgänge im Fenster **Befehl** ausführen. Wenn die Werte der Variablen `varA` und `varB` beispielsweise unterschiedlich sind, gibt der Befehl  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 den Wert `False` zurück.  
  
## <a name="first-chance-exception-notifications"></a>Ausnahmebenachrichtigungen (erste Chance)  
 Bei einigen Einstellungskonfigurationen werden Ausnahmebenachrichtigungen (erste Chance) im Fenster **Direkt** angezeigt.  
  
#### <a name="to-toggle-first-chance-exception-notifications-in-the-immediate-window"></a>So blenden Sie Ausnahmebenachrichtigungen (erste Chance) im Direktfenster ein und aus  
  
1. Klicken Sie im Menü **Ansicht** auf **Weitere Fenster** und dann auf **Ausgabe**.  
  
2. Klicken Sie mit der rechten Maustaste auf den Textbereich des **Ausgabefensters**, und aktivieren bzw. deaktivieren Sie die Option **Ausnahmemeldungen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Navigieren im Code mit dem Debugger](../../debugger/navigating-through-code-with-the-debugger.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Debuggen in Visual Studio](../../debugger/debugging-in-visual-studio.md)   
 [Debugger – Grundlagen](../../debugger/debugger-basics.md)   
 [Exemplarische Vorgehensweise: Debuggen zur Entwurfszeit](../../debugger/walkthrough-debugging-at-design-time.md)   
 [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)   
 [Verwenden von regulären Ausdrücken in Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)
