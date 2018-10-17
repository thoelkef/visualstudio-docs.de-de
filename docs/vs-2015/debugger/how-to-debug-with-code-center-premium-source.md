---
title: 'Vorgehensweise: Debuggen mit Code Center Premium-Quellcode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Code Center Premium
- debugging [Visual Studio], Code Center Premium
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3fa890e15a27a3d54c420520a71119f794fd124c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248265"
---
# <a name="how-to-debug-with-code-center-premium-source"></a>Gewusst wie: Debuggen mit Code Center Premium-Quellcode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]-Debugger können Sie sicheren, freigegebenen Microsoft MSDN Code Center Premium-Quellcode debuggen.  
  
 In diesem Thema wird erläutert, wie Sie Code Center Premium in Visual Studio einrichten und den Quellcode debuggen.  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>So bereiten Sie Debuggen mit Code Center Premium vor  
  
1.  Schließen Sie das SmartCard-Lesegerät an, und setzen Sie die Karte ein, die Sie von der Initiative für freigegebene Quellen erhalten haben.  
  
2.  Starten Sie Visual Studio.  
  
3.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
4.  In der **Optionen** öffnen Sie im Dialogfeld die **Debuggen** Knoten, und klicken Sie auf **allgemeine**.  
  
5.  Deaktivieren der **nur eigenen Code aktivieren (nur verwaltet)** Kontrollkästchen.  
  
6.  Wählen Sie **Quellserverunterstützung aktivieren**.  
  
7.  Klare **Quelldateien müssen genau mit übereinstimmen, die ursprüngliche Version**.  
  
8.  Unter den **Debuggen** Knoten, klicken Sie auf **Symbole**.  
  
9. In der **Symboldateien (PDB) Speicherorte** das Kontrollkästchen der **Microsoft Server-Symbole** das Kontrollkästchen, und fügen Sie die folgenden Speicherorte:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Achten Sie darauf, dass Sie den nachgestellten Schrägstrich**/** am Ende des Pfads.  
  
     Verschieben Sie diese Orte an den Anfang der Liste, um sicherzustellen, dass diese Symbole zuerst geladen werden.  
  
    > [!NOTE]
    >  Diese Code Center Premium-Orte müssen zuerst aufgeführt werden, damit sie als erste Orte geladen werden. In Visual Studio 2010 können nicht verschoben werden alle oben aufgeführten Server die **Microsoft-Symbolserver** Eintrag, weshalb Sie das Kontrollkästchen deaktiviert werden muss.  
    >   
    >  Um während einer Debugsitzung Symbole aus den Microsoft-Symbolen zu laden, folgen Sie diesen Schritten:  
    >   
    >  1.  Auf der **Debuggen** Menü wählen **Windows** und wählen Sie dann **Module**.  
    > 2.  Wählen Sie das Modul aus, für dass Sie Symbole möchten, und öffnen Sie dann das Kontextmenü. Wählen Sie **Symbole laden aus** und wählen Sie dann **Microsoft-Symbolserver**.  
  
10. In der **Symbole vom Symbolserver in diesem Verzeichnis zwischenspeichern** Geben Sie einen Speicherort wie z. B. `C:\symbols` Code Center Premium können, wo die Symbole zwischengespeichert. Das Zwischenspeichern von Symbolen kann die Leistung während des Debuggens erheblich verbessern.  
  
     Wenn beim Debuggen von Quellcode Schwierigkeiten mit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] auftreten, nachdem Sie diese Schritte abgeschlossen haben, überprüfen Sie den Cacheort für zuvor zwischengespeicherte und veraltete Symboldateien. Entfernen Sie die veralteten Symboldateien.  
  
11. Klicken Sie auf **OK**.  
  
12. Starten Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] neu, um sicherzustellen, dass Einstellungen beibehalten werden.  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>So debuggen Sie den Quellcode mithilfe der Funktion "An den Prozess anhängen"  
  
1.  Schließen Sie das SmartCard-Lesegerät an, und setzen Sie die Karte ein, die Sie von der Initiative für freigegebene Quellen erhalten haben.  
  
2.  Starten Sie Visual Studio.  
  
3.  Öffnen Sie Ihr Visual Studio-Projekt.  
  
4.  Auf der **Tools** Menü klicken Sie auf **an den Prozess anhängen**.  
  
5.  In der **an den Prozess anhängen** Dialogfeld klicken Sie auf **wählen**.  
  
6.  In der **Codetyp auswählen** Dialogfeld **Codetypen**Option **Native**, **verwaltete**, und **verwaltet ( v4. 0)**.  
  
7.  Klicken Sie auf **OK** zum Verwerfen der **Codetyp auswählen** Dialogfeld.  
  
8.  In der **verfügbare Prozesse** Feld, wählen Sie den Prozess, die Sie debuggen möchten.  
  
9. Klicken Sie auf **Anfügen**aus.  
  
10. Wenn Sie aufgefordert werden, die das Zertifikat zu bestätigen, klicken Sie auf **OK**. Geben Sie anschließend die PIN ein. Übernehmen Sie die Nutzungsbedingungen für Code Center Premium, wenn Sie dazu aufgefordert werden.  
  
     Das Herunterladen von Symbolen kann je nach Netzwerkgeschwindigkeit viel Zeit in Anspruch nehmen. Auf der Statusleiste wird angezeigt, wenn alle Symbole erfolgreich heruntergeladen wurden.  
  
11. Wiederholen Sie die Anfügeschritte für alle verwalteten Projekte in der Lösung.  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>So debuggen Sie Quellcode von einer vorhandenen Lösung aus  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die Projektmappe, und wählen Sie dann **Eigenschaften**.  
  
2.  Wählen Sie im Dialogfeld Eigenschaftenseiten für Projektmappen **Quelldateien debuggen** in die **allgemeine Eigenschaften** Knoten.  
  
3.  Hinzufügen von folgendem Speicherort auf dem **Verzeichnisse mit Quelldateien** Liste:  
  
     `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Achten Sie darauf, dass Sie den nachgestellten Schrägstrich**/** am Ende des Pfads.  
  
4.  Führen Sie für jedes verwaltete Projekte in der Projektmappe Folgendes aus:  
  
    1.  Klicken Sie im Projektmappen-Explorer das Kontextmenü für das Projekt, und wählen Sie dann **Eigenschaften**.  
  
    2.  Wählen Sie **Debuggen** und wählen Sie dann **nicht verwaltetes Codedebuggen aktivieren**.  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>So erstellen Sie die Lösung mit der Code Center Premium-Quelle  
  
1.  Legen Sie in der `Package`-Klasse einen Haltepunkt für den Paketkonstruktor fest.  
  
2.  In der `Debug` Menü klicken Sie auf **Debuggen starten**.  
  
3.  Wenn Sie den Haltepunkt im Paketkonstruktor erreichen, navigieren Sie zu der **Aufrufliste** Fenster, und mit der rechten Maustaste der Stapelrahmen, der zu ladenden Assembly Symbole klicken Sie dann aus, klicken Sie auf **Symbole laden**.  
  
     Doppelklicken Sie auf den Aufrufframe, um die Quelle zu laden.  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>So durchsuchen Sie Quellcode in Code Center Premium  
  
1.  Schließen Sie das SmartCard-Lesegerät an, und setzen Sie die Karte ein, die Sie von der Initiative für freigegebene Quellen erhalten haben.  
  
2.  Starten Sie Internet Explorer, und geben Sie die folgende URL ein: `https://codepremium.msdn.microsoft.com`  
  
3.  Navigieren Sie zur gewünschten Quelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Code Center Premium](http://www.microsoft.com/resources/sharedsource/ccp.mspx)



