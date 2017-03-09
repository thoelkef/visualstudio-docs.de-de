---
title: "Fenster &quot;Arbeitsspeicher&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.memory"
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
  - "Speicherfenster"
  - "Zeichenfolgen [Visual Studio], anzeigen"
  - "Debugger [Visual Studio], Fenster „Arbeitsspeicher“"
  - "Arbeitsspeicher [Visual Studio], Debuggen"
  - "Debuggen [Visual Studio], Fenster „Arbeitsspeicher“"
  - "Puffer, anzeigen"
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fenster &quot;Arbeitsspeicher&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Fenster **Arbeitsspeicher** stellt eine Ansicht des von der Anwendung belegten Arbeitsspeichers zur Verfügung.  Im Fenster **Überwachung**, Dialogfeld**QuickWatch**, Fenster **Auto** und Fenster **Lokal** wird der Inhalt der Variablen angezeigt, die an bestimmten Orten im Arbeitsspeicher gespeichert werden.  Im Fenster **Arbeitsspeicher** wird jedoch das umfangreiche Bild angezeigt.  Diese Ansicht ist besonders angenehm beim Untersuchen von großen Datenmengen \(beispielsweise Puffer oder umfangreiche Zeichenfolgen\), die in den anderen Fenstern nicht gut dargestellt werden.  Das Fenster **Arbeitsspeicher** ist jedoch nicht auf die Anzeige von Daten beschränkt.  Darin wird der gesamte Inhalt des Arbeitsspeichers angezeigt, unabhängig davon, ob es sich dabei um Daten, Code oder um zufällig verteilte Objekte in nicht zugewiesenem Arbeitsspeicher handelt.  
  
 Das Fenster **Arbeitsspeicher** ist nur verfügbar, wenn Debuggen auf Adressebene im Dialogfeld **Optionen** im Knoten **Debuggen** aktiviert ist.  Das Fenster **Arbeitsspeicher** ist jedoch nicht für Skriptsprachen oder SQL verfügbar, da diese Sprachen das Speicherkonzept nicht unterstützen.  
  
## Öffnen eines Arbeitsspeicherfensters  
  
#### So öffnen Sie ein Arbeitsspeicherfenster  
  
1.  Beginnen Sie mit dem Debuggen, sofern Sie den Debugmodus noch nicht ausgewählt haben.  
  
2.  Zeigen Sie im Menü **Debuggen** auf **Fenster**.  Zeigen Sie anschließend auf **Arbeitsspeicher**, und klicken Sie dann auf **Arbeitsspeicher 1**, **Arbeitsspeicher 2**, **Arbeitsspeicher 3** oder auf **Arbeitsspeicher 4**. \(Editionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auf niedrigerer Ebene nur ein einzelnes Fenster mit der Bezeichnung **Arbeitsspeicher**.  Wenn Sie eine dieser Editionen verwenden, klicken Sie einfach auf **Arbeitsspeicher**\).  
  
## Paging im Fenster "Arbeitsspeicher"  
 Das Fenster **Arbeitsspeicher** beinhaltet eine vertikale Schiebeleiste, die eine nicht standardmäßige Funktionsweise besitzt.  Der Adressbereich eines modernen Computers ist sehr groß, und eine Suche kann leicht fehlschlagen, wenn Sie das Bildlauffeld der Bildlaufleiste an eine zufällige Position ziehen.  Aus diesem Grunde verhält sich das Bildlauffeld, als wäre es beidseitig mit einer Zugfeder verbunden, und verbleibt stets in der Mitte der Bildlaufleiste.  In Anwendungen, die in systemeigenem Code geschrieben sind, können Sie einen Bildlauf nach oben oder unten durchführen; die Durchführung eines freien Bildlaufs ist jedoch nicht möglich.  
  
 Höhere Speicheradressen werden unten im Fenster angezeigt.  Um eine höhere Adresse anzuzeigen, führen Sie einen Bildlauf nach unten anstatt nach oben aus.  
  
#### So führen Sie im Speicher einen Bildlauf nach oben oder nach unten durch  
  
1.  Klicken Sie unter dem Ziehpunkt in der vertikalen Bildlaufleiste, um einen Bildlauf nach unten auszuführen \(Navigieren zu einer höheren Speicheradresse\).  
  
2.  Für einen Bildlauf nach oben \(Navigieren zu einer niedrigeren Speicheradresse\) klicken Sie über dem Bildlauffeld auf der vertikalen Bildlaufleiste.  
  
## Auswählen eines Arbeitsspeicherorts  
 Wenn Sie sofort zu einer ausgewählten Speicherbereich wechseln möchten, können Sie den entsprechenden Wert im Feld **Adresse** bearbeiten oder dazu Drag & Drop verwenden.  Das Feld **Adresse** nimmt nicht nur numerische Werte an, sondern auch Ausdrücke, die als Adressen ausgewertet werden.  Standardmäßig wird im Fenster **Arbeitsspeicher** ein Ausdruck im Feld **Adresse** als Live\-Ausdruck behandelt, der bei der Ausführung des Programms erneut ausgewertet wird.  Live\-Ausdrücke können sehr hilfreich sein.  Sie können beispielsweise dazu verwendet werden, den Speicher anzuzeigen, auf den ein Zeiger verweist.  
  
#### So wählen Sie einen Arbeitsspeicherort per Drag & Drop aus  
  
1.  Wählen Sie in einem beliebigen Fenster eine Speicheradresse oder eine Zeigervariable aus, die eine Speicheradresse enthält.  
  
2.  Ziehen Sie die Adresse oder den Zeiger auf das Fenster **Arbeitsspeicher**.  
  
#### So wählen Sie eine Speicheradresse durch Eingeben aus  
  
1.  Klicken Sie im Fenster **Arbeitsspeicher** in das Feld **Adresse**.  
  
2.  Geben Sie die gewünschte Adresse manuell oder über den Befehl Einfügen ein, und drücken Sie anschließend die **EINGABETASTE**.  
  
## Ändern der Anzeigemethode für Informationen im Fenster "Arbeitsspeicher"  
 Die Art und Weise der Anzeige des Speicherinhalts im Fenster **Arbeitsspeicher** kann angepasst werden.  Standardmäßig wird der Speicherinhalt in Form einer ganzen Zahl mit 1 Byte im Hexadezimalformat angezeigt. Die Anzahl der Spalten wird automatisch durch die aktuelle Breite des Fensters bestimmt.  
  
#### So ändern Sie das Format des Speicherinhalts  
  
1.  Klicken Sie mit der rechten Maustaste in das Fenster **Arbeitsspeicher**.  
  
2.  Wählen Sie das gewünschte Format aus.  
  
#### So ändern Sie die Anzahl der Spalten im Fenster "Arbeitsspeicher"  
  
1.  Suchen Sie auf der Symbolleiste des Fensters **Arbeitsspeicher** die Liste **Spalten**.  
  
2.  Wählen Sie in der Liste **Spalten** die Anzahl anzuzeigender Spalten aus. Sie können auch **Automatisch** auswählen, um eine automatische Anpassung an die Breite des Fensters vorzunehmen.  
  
 Wenn sich der Inhalt des Fensters **Arbeitsspeicher** während der Ausführung des Programms nicht ändern soll, können Sie die Live\-Auswertung von Ausdrücken deaktivieren.  
  
#### So schalten Sie die Liveauswertung um  
  
1.  Klicken Sie mit der rechten Maustaste in das Fenster **Arbeitsspeicher**.  
  
2.  Klicken Sie im Kontextmenü auf **Automatisch neu auswerten**.  
  
     Wenn die Live\-Auswertung aktiv ist, ist die Option ausgewählt. Indem Sie auf die Option klicken, wird die Live\-Auswertung ausgeschaltet.  Wenn die Live\-Auswertung deaktiviert ist, ist die Option nicht ausgewählt, und indem Sie auf die Option klicken, wird die Live\-Auswertung eingeschaltet.  
  
 Die Symbolleiste am oberen Rand des Fensters **Arbeitsspeicher** kann angezeigt oder ausgeblendet werden.  Sie können nicht auf das Adressfeld oder andere Tools zugreifen, wenn die Symbolleiste ausgeblendet ist.  
  
#### So blenden Sie die Symbolleiste ein oder aus  
  
1.  Klicken Sie mit der rechten Maustaste in das Fenster **Arbeitsspeicher**.  
  
2.  Klicken Sie im Kontextmenü auf **Symbolleiste anzeigen**.  
  
     Je nach ihrem vorherigen Zustand wird die Symbolleiste ein\- bzw. ausgeblendet.  
  
## Verfolgen eines Zeigers im Arbeitsspeicher  
 In Anwendungen, die im systemeigenen Code geschrieben wurden, können Sie als Live\-Ausdrücke Registernamen verwenden.  Zur Verfolgung des Stapels können Sie z. B. den Stapelzeiger verwenden.  
  
#### So verfolgen Sie einen Zeiger im Arbeitsspeicher  
  
1.  Geben Sie im Fenster **Arbeitsspeicher** im Feld **Adresse** einen Zeigerausdruck ein.  Die Zeigervariable muss sich im aktuellen Gültigkeitsbereich befinden.  Je nach verwendeter Sprache müssen Sie u. U. den entsprechenden Verweis aufheben.  
  
2.  Drücken Sie die **EINGABETASTE**.  
  
     Wenn Sie anschließend einen Ausführungsbefehl wie **Schritt** verwenden, ändert sich die angezeigte Speicheradresse automatisch entsprechend der Zeigerbewegung.  
  
## Siehe auch  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)