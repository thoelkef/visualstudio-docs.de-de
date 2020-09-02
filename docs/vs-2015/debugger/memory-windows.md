---
title: Arbeitsspeicher Fenster | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.memory
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e60f9b3c9acf1377139fee27486bb10251d8804a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158471"
---
# <a name="memory-windows"></a>Fenster "Arbeitsspeicher"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Fenster Arbeits **Speicher** bietet einen Einblick in den von der Anwendung verwendeten Speicherplatz. Das Fenster "über **Wachen** ", das Fenster " **schnell Überwachung** ", **das Fenster "** Auto **" und das** Fenster "lokal" zeigen den Inhalt von Variablen an, die an bestimmten Speicherorten gespeichert sind. Das Fenster "Arbeitsspeicher" zeigt jedoch das umfangreiche Bild **an** . Diese Ansicht ist besonders angenehm beim Untersuchen von großen Datenmengen (beispielsweise Puffer oder umfangreiche Zeichenfolgen), die in den anderen Fenstern nicht gut dargestellt werden. Das Fenster "Arbeits **Speicher** " ist jedoch nicht auf die Anzeige von Daten beschränkt. Darin wird der gesamte Inhalt des Arbeitsspeichers angezeigt, unabhängig davon, ob es sich dabei um Daten, Code oder um zufällig verteilte Objekte in nicht zugewiesenem Arbeitsspeicher handelt.  
  
 Das Fenster Arbeits **Speicher** ist nur verfügbar, wenn Debuggen auf Adress Ebene im Dialogfeld **Optionen** ,**Debuggen** , aktiviert ist. Das Fenster "Arbeits **Speicher** " ist für Skripts oder SQL nicht verfügbar, bei denen es sich um Sprachen handelt, die das Arbeitsspeicher Konzept nicht erkennen.  
  
## <a name="opening-a-memory-window"></a>Öffnen eines Arbeitsspeicherfensters  
  
#### <a name="to-open-a-memory-window"></a>So öffnen Sie ein Arbeitsspeicherfenster  
  
1. Beginnen Sie mit dem Debuggen, sofern Sie den Debugmodus noch nicht ausgewählt haben.  
  
2. Zeigen Sie im Menü **Debuggen** auf **Fenster**. Zeigen Sie dann auf Arbeits **Speicher** , und klicken Sie dann auf Arbeitsspeicher **1**, Arbeits **Speicher 2**, Arbeits **Speicher 3**oder Arbeits **Speicher 4**. (Editionen auf niedrigerer Ebene von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] haben nur ein einzelnes Arbeits **Speicher** Fenster. Wenn Sie eine dieser Editionen verwenden, klicken Sie einfach auf Arbeits **Speicher**.)  
  
## <a name="paging-in-the-memory-window"></a>Paging im Fenster "Arbeitsspeicher"  
 Das Fenster "Arbeits **Speicher** " verfügt über eine vertikale Scrollleiste, die nicht standardmäßig funktioniert. Der Adressbereich eines modernen Computers ist sehr groß, und eine Suche kann leicht fehlschlagen, wenn Sie das Bildlauffeld der Bildlaufleiste an eine zufällige Position ziehen. Aus diesem Grunde verhält sich das Bildlauffeld, als wäre es beidseitig mit einer Zugfeder verbunden, und verbleibt stets in der Mitte der Bildlaufleiste. In Anwendungen, die in systemeigenem Code geschrieben sind, können Sie einen Bildlauf nach oben oder unten durchführen; die Durchführung eines freien Bildlaufs ist jedoch nicht möglich.  
  
 Höhere Speicheradressen werden unten im Fenster angezeigt. Um eine höhere Adresse anzuzeigen, führen Sie einen Bildlauf nach unten anstatt nach oben aus.  
  
#### <a name="to-page-up-or-down-in-memory"></a>So führen Sie im Speicher einen Bildlauf nach oben oder nach unten durch  
  
1. Klicken Sie unter dem Ziehpunkt in der vertikalen Scrollleiste, um einen Bildlauf nach unten auszuführen (Navigieren zu einer höheren Speicheradresse).  
  
2. Für einen Bildlauf nach oben (Navigieren zu einer niedrigeren Speicheradresse) klicken Sie über dem Bildlauffeld auf der vertikalen Bildlaufleiste.  
  
## <a name="selecting-a-memory-location"></a>Auswählen eines Arbeitsspeicherorts  
 Wenn Sie sofort zu einem ausgewählten Speicherort im Arbeitsspeicher wechseln möchten, können Sie dazu einen Drag & Drop-Vorgang verwenden oder den Wert im Feld **Adresse** bearbeiten. Das **Adress** Feld akzeptiert nicht nur numerische Werte, sondern auch Ausdrücke, die als Adressen ausgewertet werden. Standardmäßig behandelt das Arbeits **Speicher** Fenster einen **Adress** Ausdruck als Live Ausdruck, der bei der Ausführung des Programms erneut ausgewertet wird. Live-Ausdrücke können sehr hilfreich sein. Sie können beispielsweise dazu verwendet werden, den Speicher anzuzeigen, auf den ein Zeiger verweist.  
  
#### <a name="to-select-a-memory-location-by-dragging-and-dropping"></a>So wählen Sie einen Arbeitsspeicherort per Drag &amp; Drop aus  
  
1. Wählen Sie in einem beliebigen Fenster eine Speicheradresse oder eine Zeigervariable aus, die eine Speicheradresse enthält.  
  
2. Ziehen Sie die Adresse oder den Zeiger in das Fenster Arbeits **Speicher** .  
  
#### <a name="to-select-a-memory-location-by-editing"></a>So wählen Sie eine Speicheradresse durch Eingeben aus  
  
1. Wählen Sie im Fenster Arbeits **Speicher** das Feld **Adresse** aus.  
  
2. Geben Sie die gewünschte Adresse ein, oder fügen Sie Sie ein, und drücken Sie dann die **Eingabe**Taste.  
  
## <a name="changing-the-way-the-memory-window-displays-information"></a>Ändern der Anzeigemethode für Informationen im Fenster "Arbeitsspeicher"  
 Die Art und Weise der Anzeige des Speicherinhalts im Fenster **Arbeitsspeicher** kann angepasst werden. Standardmäßig wird der Speicherinhalt in Form einer ganzen Zahl mit 1 Byte im Hexadezimalformat angezeigt. Die Anzahl der Spalten wird automatisch durch die aktuelle Breite des Fensters bestimmt.  
  
#### <a name="to-change-the-format-of-the-memory-contents"></a>So ändern Sie das Format des Speicherinhalts  
  
1. Klicken Sie mit der rechten Maustaste auf das Fenster Arbeits **Speicher** .  
  
2. Wählen Sie das gewünschte Format aus.  
  
#### <a name="to-change-the-number-of-columns-in-the-memory-window"></a>So ändern Sie die Anzahl der Spalten im Fenster "Arbeitsspeicher"  
  
1. Suchen Sie in der Symbolleiste am oberen Rand des Fensters Arbeits **Speicher** die Liste **Spalten** .  
  
2. Wählen Sie in der Liste **Spalten** die Anzahl der Spalten aus, die Sie anzeigen möchten, oder wählen Sie **automatisch** für automatische Anpassung aus, um die Breite des Fensters anzupassen.  
  
   Wenn Sie nicht möchten, dass sich der Inhalt des Fensters " **Speicher** " ändert, während das Programm ausgeführt wird, können Sie die Live Ausdrucks Auswertung deaktivieren.  
  
#### <a name="to-toggle-live-evaluation"></a>So schalten Sie die Liveauswertung um  
  
1. Klicken Sie mit der rechten Maustaste auf das Fenster Arbeits **Speicher** .  
  
2. Klicken Sie im Kontextmenü auf **automatisch neu auswerten**.  
  
    Wenn die Live-Auswertung aktiv ist, ist die Option ausgewählt. Indem Sie auf die Option klicken, wird die Live-Auswertung ausgeschaltet. Wenn die Live-Auswertung deaktiviert ist, ist die Option nicht ausgewählt, und indem Sie auf die Option klicken, wird die Live-Auswertung eingeschaltet.  
  
   Die Symbolleiste am oberen Rand des Fensters **Arbeitsspeicher** kann angezeigt oder ausgeblendet werden. Sie können nicht auf das Adressfeld oder andere Tools zugreifen, wenn die Symbolleiste ausgeblendet ist.  
  
#### <a name="to-toggle-the-toolbar"></a>So blenden Sie die Symbolleiste ein oder aus  
  
1. Klicken Sie mit der rechten Maustaste auf ein Arbeits **Speicher** Fenster.  
  
2. Klicken Sie im Kontextmenü auf **Symbolleiste anzeigen**.  
  
     Je nach ihrem vorherigen Zustand wird die Symbolleiste ein- bzw. ausgeblendet.  
  
## <a name="following-a-pointer-through-memory"></a>Verfolgen eines Zeigers im Arbeitsspeicher  
 In Anwendungen, die im nativen Code geschrieben wurden, können Sie als Live-Ausdrücke Registernamen verwenden. Zur Verfolgung des Stapels können Sie z. B. den Stapelzeiger verwenden.  
  
#### <a name="to-follow-a-pointer-through-memory"></a>So verfolgen Sie einen Zeiger im Arbeitsspeicher  
  
1. Geben Sie im Feld **Adress** Feld des Arbeits **Speichers** einen Zeiger Ausdruck ein. Die Zeigervariable muss sich im aktuellen Gültigkeitsbereich befinden. Je nach verwendeter Sprache müssen Sie u. U. den entsprechenden Verweis aufheben.  
  
2. Drücken Sie die **EINGABETASTE**.  
  
     Wenn Sie nun einen Ausführungs Befehl wie **Step**verwenden, ändert sich die angezeigte Speicheradresse automatisch, wenn sich der Zeiger ändert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)
