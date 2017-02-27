---
title: "Gewusst wie: Debuggen mit Code Center Premium-Quellcode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
helpviewer_keywords: 
  - "Code Center Premium"
  - "Debuggen [Visual Studio], Code Center Premium"
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Gewusst wie: Debuggen mit Code Center Premium-Quellcode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit dem [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]\-Debugger können Sie sicheren, freigegebenen Microsoft MSDN Code Center Premium\-Quellcode debuggen.  
  
 In diesem Thema wird erläutert, wie Sie Code Center Premium in Visual Studio einrichten und den Quellcode debuggen.  
  
### So bereiten Sie Debuggen mit Code Center Premium vor  
  
1.  Schließen Sie das SmartCard\-Lesegerät an, und setzen Sie die Karte ein, die Sie von der Initiative für freigegebene Quellen erhalten haben.  
  
2.  Starten Sie Visual Studio.  
  
3.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
4.  Erweitern Sie im Dialogfeld **Optionen** den Knoten **Debuggen**, und klicken Sie auf **Allgemein**.  
  
5.  Deaktivieren Sie das Kontrollkästchen **Nur eigenen Code aktivieren \(nur verwaltet\)**.  
  
6.  Wählen Sie **Quellserverunterstützung aktivieren** aus.  
  
7.  Deaktivieren Sie das Kontrollkästchen **Quelldateien müssen exakt mit der Originalversion übereinstimmen**.  
  
8.  Klicken Sie unter dem Knoten **Debugging** auf **Symbole**.  
  
9. Deaktivieren Sie im Feld **Orte für Symboldateien \(PDB\):** das Kontrollkästchen **Microsoft Server\-Symbole**, und fügen Sie die folgenden Orte hinzu:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Achten Sie darauf, den nachgestellten Schrägstrich **\/** am Ende des Pfads anzugeben.  
  
     Verschieben Sie diese Orte an den Anfang der Liste, um sicherzustellen, dass diese Symbole zuerst geladen werden.  
  
    > [!NOTE]
    >  Diese Code Center Premium\-Orte müssen zuerst aufgeführt werden, damit sie als erste Orte geladen werden.  In Visual Studio 2010 können Sie keine Server über den Eintrag **Microsoft\-Symbolserver** hinaus verschieben. Deshalb müssen Sie das Kontrollkästchen deaktivieren.  
    >   
    >  Um während einer Debugsitzung Symbole aus den Microsoft\-Symbolen zu laden, folgen Sie diesen Schritten:  
    >   
    >  1.  Wählen Sie im Menü **Debuggen** die Option **Fenster** aus, und wählen Sie dann **Module**.  
    > 2.  Wählen Sie das Modul aus, für dass Sie Symbole möchten, und öffnen Sie dann das Kontextmenü.  Wählen Sie **Symbole laden aus**, und wählen Sie dann **Microsoft\-Symbolserver**.  
  
10. Geben Sie im Feld **Symbole vom Symbolserver in diesem Verzeichnis zwischenspeichern** einen Ort an \(z. B. `C:\symbols`\), in dem Symbole von Code Center Premium zwischengespeichert werden können.  Das Zwischenspeichern von Symbolen kann die Leistung während des Debuggens erheblich verbessern.  
  
     Wenn beim Debuggen von Quellcode Schwierigkeiten mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auftreten, nachdem Sie diese Schritte abgeschlossen haben, überprüfen Sie den Cacheort für zuvor zwischengespeicherte und veraltete Symboldateien.  Entfernen Sie die veralteten Symboldateien.  
  
11. Klicken Sie auf **OK**.  
  
12. Starten Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] neu, um sicherzustellen, dass Einstellungen beibehalten werden.  
  
### So debuggen Sie den Quellcode mithilfe der Funktion "An den Prozess anhängen"  
  
1.  Schließen Sie das SmartCard\-Lesegerät an, und setzen Sie die Karte ein, die Sie von der Initiative für freigegebene Quellen erhalten haben.  
  
2.  Starten Sie Visual Studio.  
  
3.  Öffnen Sie Ihr Visual Studio\-Projekt.  
  
4.  Klicken Sie im Menü **Extras** auf **An den Prozess anhängen**.  
  
5.  Klicken Sie im Dialogfeld **An den Prozess anhängen** auf **Auswählen**.  
  
6.  Wählen Sie im Dialogfeld **Codetyp auswählen** unter **Codetypen finden** die Option **Systemeigen**, **Verwaltet** und **Managed\(v4.0\)** aus.  
  
7.  Klicken Sie auf **OK**, um das Dialogfeld **Codetyp auswählen** zu schließen.  
  
8.  Wählen Sie im Feld **Verfügbare Prozesse** den Prozess aus, den Sie debuggen möchten.  
  
9. Klicken Sie auf **Anfügen**.  
  
10. Wenn Sie aufgefordert werden, das Zertifikat zu bestätigen, klicken Sie auf **OK**.  Geben Sie anschließend die PIN ein.  Übernehmen Sie die Nutzungsbedingungen für Code Center Premium, wenn Sie dazu aufgefordert werden.  
  
     Das Herunterladen von Symbolen kann je nach Netzwerkgeschwindigkeit viel Zeit in Anspruch nehmen.  Auf der Statusleiste wird angezeigt, wenn alle Symbole erfolgreich heruntergeladen wurden.  
  
11. Wiederholen Sie die Anfügeschritte für alle verwalteten Projekte in der Lösung.  
  
### So debuggen Sie Quellcode von einer vorhandenen Lösung aus  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für die Projektmappe, und wählen Sie dann **Eigenschaften** aus.  
  
2.  Wählen Sie im Dialogfeld "Eigenschaftenseiten" für Projektmappen im Knoten **Allgemeine Eigenschaften** die Option **Quelldateien debuggen**, aus.  
  
3.  Fügen Sie der Liste **Verzeichnisse mit Quelldateien** den folgenden Ort hinzu:  
  
     `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Achten Sie darauf, den nachgestellten Schrägstrich **\/** am Ende des Pfads anzugeben.  
  
4.  Führen Sie für jedes verwaltete Projekte in der Projektmappe Folgendes aus:  
  
    1.  Öffnen Sie im Projektmappen\-Explorer das Kontextmenü für das Projekt, und wählen Sie **Eigenschaften** aus.  
  
    2.  Wählen Sie **Debuggen** und dann **Debuggen von nicht verwaltetem Code aktivieren** aus.  
  
### So erstellen Sie die Lösung mit der Code Center Premium\-Quelle  
  
1.  Legen Sie in der `Package`\-Klasse einen Haltepunkt für den Paketkonstruktor fest.  
  
2.  Klicken Sie im Menü `Debug` auf **Debugging starten**.  
  
3.  Wenn Sie den Haltepunkt im Paketkonstruktor erreichen, navigieren Sie zum Fenster **Aufrufliste**, und klicken Sie mit der rechten Maustaste auf den Stapelrahmen der Assembly, aus der Sie Symbole laden möchten, und klicken Sie anschließend auf **Symbole laden**.  
  
     Doppelklicken Sie auf den Aufrufframe, um die Quelle zu laden.  
  
### So durchsuchen Sie Quellcode in Code Center Premium  
  
1.  Schließen Sie das SmartCard\-Lesegerät an, und setzen Sie die Karte ein, die Sie von der Initiative für freigegebene Quellen erhalten haben.  
  
2.  Starten Sie Internet Explorer, und geben Sie die folgende URL ein: `https://codepremium.msdn.microsoft.com`  
  
3.  Navigieren Sie zur gewünschten Quelle.  
  
## Siehe auch  
 [Einstellungen und Vorbereitung für das Debuggen](../debugger/debugger-settings-and-preparation.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Code Center Premium](http://www.microsoft.com/resources/sharedsource/ccp.mspx)