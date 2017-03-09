---
title: "Anzeigen von Datenwerten als Datentipps im Code-Editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DataTips (Tool)"
  - "Debuggen [Visual Studio], DataTips"
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Anzeigen von Datenwerten als Datentipps im Code-Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

DataTips stellen eine praktische Möglichkeit dar, um beim Debuggen Informationen über Variablen im Programm anzuzeigen.  Sie können DataTips nur im Unterbrechungsmodus verwenden und nur mit Variablen, die sich im aktuellen Gültigkeitsbereich der Ausführung befinden.  
  
 In [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] können DataTips an einer bestimmten Position in einer Quelldatei angeheftet werden, oder sie können über allen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Fenstern unverankert angezeigt werden.  
  
### So zeigen Sie DataTips an \(nur im Unterbrechungsmodus\)  
  
1.  Platzieren Sie in einem Quellcodefenster den Mauszeiger auf eine beliebige Variable aus dem aktuellen Gültigkeitsbereich.  
  
     Ein DataTip wird angezeigt.  
  
    > [!NOTE]
    >  DataTips werden immer in dem Kontext ausgeführt, in dem die Ausführung angehalten wird, und nicht an der Stelle, auf die der Cursor zeigt.  Wenn Sie in einer anderen Funktion auf eine Variable mit dem Namen einer Variablen im aktuellen Kontext zeigen, wird der Wert der Variablen in der anderen Funktion als der Wert der Variablen im aktuellen Kontext angezeigt.  
  
2.  Der DataTip verschwindet, wenn Sie den Mauszeiger fortbewegen.  Um den DataTip anzuheften, sodass er geöffnet bleibt, klicken Sie auf das Symbol **An Quelle heften**.  
  
    -   Oder klicken Sie mit der rechten Maustaste auf eine Variable, und klicken Sie dann auf **An Quelle heften**.  
  
     Der angeheftete DataTip wird geschlossen, wenn die Debugsitzung endet.  
  
### So lösen Sie einen DataTip und zeigen diesen unverankert an  
  
-   Klicken Sie in einem angehefteten DataTip auf das Symbol **Von Quelle lösen**.  
  
     Das Pinsymbol ändert sich in die gelöste Position.  Der DataTip wird nun unverankert über allen geöffneten Fenstern angezeigt.  Der unverankerte DataTip wird geschlossen, wenn die Debugsitzung endet.  
  
### So heften Sie einen unverankerten DataTip wieder an  
  
-   Klicken Sie in einem DataTip auf das Pinsymbol.  
  
     Das Pinsymbol ändert sich in die angeheftete Position.  Wenn sich der DataTip außerhalb eines Quellcodefensters befindet, wird das Pinsymbol deaktiviert, und der DataTip kann nicht angeheftet werden.  
  
### So schließen Sie einen DataTip  
  
-   Platzieren Sie den Mauszeiger auf einem DataTip, und klicken Sie dann auf das Symbol **Schließen**.  
  
### So schließen Sie alle DataTips  
  
-   Klicken Sie im Menü **Debuggen** auf **Alle DataTips löschen**.  
  
### So schließen Sie alle DataTips für eine bestimmte Datei  
  
-   Klicken Sie im Menü **Debuggen** auf **Alle an** *File* angehefteten DataTips löschen.  
  
## Erweitern und Bearbeiten von Informationen  
 Mithilfe von DataTips können Sie ein Array, eine Struktur oder ein Objekt erweitern, um deren Member anzuzeigen.  Sie können mit einem DataTip auch den Wert einer Variablen bearbeiten.  
  
#### So erweitern Sie eine Variable, um ihre Elemente anzuzeigen  
  
-   Platzieren Sie in einem DataTip den Mauszeiger auf dem **\+** Zeichen vor dem Variablennamen.  
  
     Die Variable wird erweitert, und die Elemente werden in Strukturansicht angezeigt.  
  
     Bei erweiterter Variable können Sie mit den Pfeiltasten der Tastatur nach oben und unten navigieren.  Sie können auch die Maus verwenden.  
  
#### So bearbeiten Sie den Wert einer Variablen mit einem DataTip  
  
1.  Klicken Sie in einem DataTip auf den Wert.  Für schreibgeschützte Werte ist diese Funktion deaktiviert.  
  
2.  Geben Sie einen neuen Wert ein, und drücken Sie die EINGABETASTE.  
  
## Transparentes Darstellen eines DataTips  
 Wenn Sie den Code hinter einem DataTip sehen möchten, können Sie dazu den DataTip vorübergehend transparent machen.  Dies gilt nicht für DataTips, die angeheftet oder unverankert sind.  
  
#### So machen Sie einen DataTip transparent  
  
-   Drücken Sie in einem DataTip STRG.  
  
     Der DataTip bleibt so lange transparent, wie Sie STRG gedrückt halten.  
  
## Visuelles Darstellen von komplexen Datentypen  
 Wenn in einem DataTip ein Vergrößerungsglassymbol neben dem Variablennamen angezeigt wird, stehen für diesen Variablentyp eine oder mehrere [Schnellansichten](../debugger/create-custom-visualizers-of-data.md) zur Verfügung.  Mit der Schnellansicht lassen sich Informationen noch übersichtlicher \(in der Regel über eine grafische Darstellung\) anzeigen.  
  
#### So zeigen Sie den Inhalt einer Variablen mithilfe der Schnellansicht an  
  
-   Klicken Sie auf das Symbol mit dem Vergrößerungsglas, um die Standardschnellansicht für den Datentyp auszuwählen.  
  
     \- oder \-  
  
     Klicken Sie auf den Popup\-Pfeil neben der Schnellansicht, und wählen Sie aus der Liste eine dem Datentyp entsprechende Schnellansicht aus.  
  
     Die Informationen werden in einer Schnellansicht angezeigt.  
  
## Hinzufügen von Informationen zu einem Überwachungsfenster  
 Wenn Sie eine Variable weiter überwachen möchten, können Sie die Variable aus einem DataTip dem **Überwachungsfenster** hinzufügen.  
  
#### So fügen Sie dem Überwachungsfenster eine Variable hinzu  
  
-   Klicken Sie mit der rechten Maustaste auf einen DataTip, und klicken Sie dann auf **Überwachung hinzufügen**.  
  
     Die Variable wird dem **Überwachungsfenster** hinzugefügt.  Wenn Sie mit einer Edition arbeiten, die mehrere **Überwachungsfenster** unterstützt, wird die Variable **Überwachen 1** hinzugefügt.  
  
## Importieren und Exportieren von DataTips  
 Sie können DataTips in eine XML\-Datei exportieren, die Sie gemeinsam mit Kollegen verwenden oder in einem Text\-Editor bearbeiten können.  
  
#### So exportieren Sie DataTips  
  
1.  Klicken Sie im Menü Debuggen auf **DataTips exportieren**.  
  
     Das Dialogfeld **DataTips exportieren** wird angezeigt.  
  
2.  Navigieren Sie mithilfe von Standarddateitechniken zu dem Verzeichnis, in dem die XML\-Datei gespeichert werden soll, geben Sie im Feld **Dateiname** einen Namen für die Datei ein, und klicken Sie dann auf **OK**.  
  
#### So importieren Sie DataTips  
  
1.  Klicken Sie im Menü Debuggen auf **DataTips importieren**.  
  
     Das Dialogfeld **DataTips importieren** wird angezeigt.  
  
2.  Suchen Sie mithilfe des Dialogfelds nach der zu öffnenden XML\-Datei, und klicken Sie auf **OK**.  
  
## Siehe auch  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Gewusst wie: Verwenden des Dialogfelds Schnellüberwachung](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Schnellansichten](../debugger/create-custom-visualizers-of-data.md)   
 [Gewusst wie: Ändern des numerischen Formats von Debuggerfenstern](../Topic/How%20to:%20Change%20the%20Numeric%20Format%20of%20Debugger%20Windows.md)