---
title: 'Gewusst wie: Debuggen mit Code Center Premium-Quelle | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db9a3e08e14e7fadca6df9e32361c0b042f565e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840871"
---
# <a name="how-to-debug-with-code-center-premium-source"></a>Gewusst wie: Debuggen mit Code Center Premium-Quellcode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]-Debugger können Sie sicheren, freigegebenen Microsoft MSDN Code Center Premium-Quellcode debuggen.  
  
 In diesem Thema wird erläutert, wie Sie Code Center Premium in Visual Studio einrichten und den Quellcode debuggen.  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>So bereiten Sie Debuggen mit Code Center Premium vor  
  
1. Schließen Sie das SmartCard-Lesegerät an, und setzen Sie die Karte ein, die Sie von der Initiative für freigegebene Quellen erhalten haben.  
  
2. Starten Sie Visual Studio.  
  
3. Klicken Sie im Menü **Extras** auf **Optionen**.  
  
4. Öffnen Sie im Dialogfeld **Optionen** den Knoten **Debuggen** , und klicken Sie auf **Allgemein**.  
  
5. Deaktivieren Sie das Kontrollkästchen **nur eigenen Code aktivieren (nur verwaltet)** .  
  
6. Wählen Sie **Quell Server Unterstützung aktivieren**aus.  
  
7. Löschen **Sie müssen Quelldateien exakt mit der ursprünglichen Version übereinstimmen**.  
  
8. Klicken Sie unter dem Knoten **Debuggen** auf **Symbole**.  
  
9. Deaktivieren Sie im Feld **Symbol Dateispeicher Orte (PDB)** das Kontrollkästchen **Microsoft-Server Symbole** , und fügen Sie die folgenden Speicherorte hinzu:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   > Stellen Sie sicher, dass Sie den nachgestellten Schrägstrich <strong>/</strong> am Ende des Pfads einschließen.  
  
     Verschieben Sie diese Orte an den Anfang der Liste, um sicherzustellen, dass diese Symbole zuerst geladen werden.  
  
   > [!NOTE]
   > Diese Code Center Premium-Orte müssen zuerst aufgeführt werden, damit sie als erste Orte geladen werden. In Visual Studio 2010 können Sie keine Server oberhalb des **Microsoft Symbol Server** -Eintrags verschieben. aus diesem Grund müssen Sie das Kontrollkästchen deaktivieren.  
   > 
   >  Um während einer Debugsitzung Symbole aus den Microsoft-Symbolen zu laden, folgen Sie diesen Schritten:  
   > 
   > 1. Klicken Sie im Menü **Debuggen** auf **Fenster** , und wählen Sie dann **Module**aus.  
   >    2.  Wählen Sie das Modul aus, für dass Sie Symbole möchten, und öffnen Sie dann das Kontextmenü. Wählen Sie **Symbole laden aus** , und wählen Sie dann **Microsoft-Symbol Server**aus.  
  
10. Geben Sie im Feld **Symbole von Symbol Servern in diesem Verzeichnis zwischenspeichern** einen Speicherort ein, z `C:\symbols` . b. wo die Symbole von Code Center Premium zwischengespeichert werden können. Das Zwischenspeichern von Symbolen kann die Leistung während des Debuggens erheblich verbessern.  
  
     Wenn beim Debuggen von Quellcode Schwierigkeiten mit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] auftreten, nachdem Sie diese Schritte abgeschlossen haben, überprüfen Sie den Cacheort für zuvor zwischengespeicherte und veraltete Symboldateien. Entfernen Sie die veralteten Symboldateien.  
  
11. Klicken Sie auf **OK**.  
  
12. Starten Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] neu, um sicherzustellen, dass Einstellungen beibehalten werden.  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>So debuggen Sie den Quellcode mithilfe der Funktion "An den Prozess anhängen"  
  
1. Schließen Sie das SmartCard-Lesegerät an, und setzen Sie die Karte ein, die Sie von der Initiative für freigegebene Quellen erhalten haben.  
  
2. Starten Sie Visual Studio.  
  
3. Öffnen Sie Ihr Visual Studio-Projekt.  
  
4. Klicken Sie **im Menü Extras** auf **an den Prozess anhängen**.  
  
5. Klicken Sie im Dialogfeld **an den Prozess anhängen** auf **auswählen**.  
  
6. Wählen Sie im Dialogfeld **Codetyp auswählen** unter **Diese Codetypen erkennen**die Option **native**, **verwaltete**und **verwaltete (v 4.0)** aus.  
  
7. Klicken Sie auf **OK** , um das Dialogfeld **Codetyp auswählen** zu schließen.  
  
8. Wählen Sie im Feld **Verfügbare Prozesse** den Prozess aus, den Sie debuggen möchten.  
  
9. Klicken Sie auf **Anfügen**aus.  
  
10. Wenn Sie zur Bestätigung Ihres Zertifikats aufgefordert werden, klicken Sie auf **OK**. Geben Sie anschließend die PIN ein. Übernehmen Sie die Nutzungsbedingungen für Code Center Premium, wenn Sie dazu aufgefordert werden.  
  
     Das Herunterladen von Symbolen kann je nach Netzwerkgeschwindigkeit viel Zeit in Anspruch nehmen. Auf der Statusleiste wird angezeigt, wenn alle Symbole erfolgreich heruntergeladen wurden.  
  
11. Wiederholen Sie die Anfügeschritte für alle verwalteten Projekte in der Lösung.  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>So debuggen Sie Quellcode von einer vorhandenen Lösung aus  
  
1. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für die Projekt Mappe, und wählen Sie dann **Eigenschaften**aus.  
  
2. Wählen Sie im Dialogfeld Projektmappen-Eigenschaften Seiten im Knoten **Allgemeine Eigenschaften** die Option **Quelldateien debuggen** aus.  
  
3. Fügen Sie der Liste **Verzeichnisse mit Quelldateien** den folgenden Speicherort hinzu:  
  
    `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   > Stellen Sie sicher, dass Sie den nachgestellten Schrägstrich <strong>/</strong> am Ende des Pfads einschließen.  
  
4. Führen Sie für jedes verwaltete Projekte in der Projektmappe Folgendes aus:  
  
   1. Öffnen Sie in Projektmappen-Explorer das Kontextmenü für das Projekt, und wählen Sie dann **Eigenschaften**aus.  
  
   2. Wählen Sie **Debuggen** und dann **Debuggen von nicht**verwalteten Code aktivieren.  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>So erstellen Sie die Lösung mit der Code Center Premium-Quelle  
  
1. Legen Sie in der `Package`-Klasse einen Haltepunkt für den Paketkonstruktor fest.  
  
2. `Debug`Klicken Sie im Menü auf **Debuggen starten**.  
  
3. Wenn Sie den Breakpoint im paketkonstruktor erreicht haben, wechseln Sie zum Fenster " **aufrufen** ", und klicken Sie mit der rechten Maustaste auf den Stapel Rahmen der Assembly, aus der Sie Symbole laden möchten, und klicken Sie dann auf **Symbole laden**.  
  
     Doppelklicken Sie auf den Aufrufframe, um die Quelle zu laden.  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>So durchsuchen Sie Quellcode in Code Center Premium  
  
1. Schließen Sie das SmartCard-Lesegerät an, und setzen Sie die Karte ein, die Sie von der Initiative für freigegebene Quellen erhalten haben.  
  
2. Starten Sie Internet Explorer, und geben Sie die folgende URL ein: `https://codepremium.msdn.microsoft.com`  
  
3. Navigieren Sie zur gewünschten Quelle.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugger-Einstellungen und-Vorbereitung](../debugger/debugger-settings-and-preparation.md)   
 [Debugger-Sicherheit](../debugger/debugger-security.md)   
 [Code Center Premium](https://www.microsoft.com/en-us/sharedsource/code-center-premium.aspx)
