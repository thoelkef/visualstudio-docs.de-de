---
title: "How to: Add, Update, or Remove a WCF Data Service Reference | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "service references [Visual Studio]"
  - "WCF Data Service reference"
  - "WCF data service references"
  - "ADO.NET service references"
  - "ADO.NET Data Service reference"
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Add, Update, or Remove a WCF Data Service Reference
Durch einen *Dienstverweis* kann ein Projekt auf einen oder mehrere [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] zugreifen.  Suchen Sie mithilfe des Dialogfelds **Dienstverweis hinzufügen** in der aktuellen Projektmappe, lokal, in einem lokalen Netzwerk oder im Internet nach [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Hinzufügen eines Dienstverweises  
  
#### So fügen Sie einen Verweis auf einen externen Dienst hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Namen des Projekts, dem der Dienst hinzugefügt werden soll. Klicken Sie dann auf **Dienstverweis hinzufügen**.  
  
     Das Dialogfeld **Dienstverweis hinzufügen** wird angezeigt.  
  
2.  Geben Sie im Feld **Adresse** die URL des Diensts ein, und klicken Sie dann auf **Gehe zu**, um nach dem Dienst zu suchen.  Wenn der Dienst eine Benutzernamen\- und Kennwortsicherheit implementiert, müssen Sie einen Benutzernamen und ein Kennwort eingeben.  
  
    > [!NOTE]
    >  Sie sollten nur auf Dienste aus einer vertrauenswürdigen Quelle verweisen.  Das Hinzufügen von Verweisen aus einer nicht vertrauenswürdigen Quelle kann die Sicherheit beeinträchtigen.  
  
     Sie können die URL auch aus der Liste **Adresse** auswählen, in der die letzten 15 URLs gespeichert sind, unter denen gültige Dienstmetadaten gefunden wurden.  
  
     Während der Suche wird eine Statusanzeige angezeigt.  Sie können die Suche jederzeit beenden, indem Sie auf die Schaltfläche **Beenden** klicken.  
  
3.  Erweitern Sie in der Liste **Dienste** den Knoten für den gewünschten Dienst, und wählen Sie eine Entitätenmenge aus.  
  
4.  Geben Sie im Feld **Namespace** den Namespace ein, den Sie für den Verweis verwenden möchten.  
  
5.  Klicken Sie auf **OK**, um dem Projekt den Verweis hinzuzufügen.  
  
     Ein Dienstclient \(Proxy\) wird generiert, und der Datei **app.config** werden Metadaten hinzugefügt, mit denen der Dienst beschrieben wird.  
  
#### So fügen Sie der aktuellen Projektmappe einen Verweis auf einen Dienst hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Namen des Projekts, dem der Dienst hinzugefügt werden soll. Klicken Sie dann auf **Dienstverweis hinzufügen**.  
  
     Das Dialogfeld **Dienstverweis hinzufügen** wird angezeigt.  
  
2.  Klicken Sie auf **Ermitteln**.  
  
     Alle Dienste \(sowohl [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] als auch WCF\-Dienste\) in der aktuellen Projektmappe werden der Liste **Dienste** hinzugefügt.  
  
3.  Erweitern Sie in der Liste **Dienste** den Knoten für den gewünschten Dienst, und wählen Sie eine Entitätenmenge aus.  
  
4.  Geben Sie im Feld **Namespace** den Namespace ein, den Sie für den Verweis verwenden möchten.  
  
5.  Klicken Sie auf **OK**, um dem Projekt den Verweis hinzuzufügen.  
  
     Ein Dienstclient \(Proxy\) wird generiert, und der Datei **app.config** werden Metadaten hinzugefügt, mit denen der Dienst beschrieben wird.  
  
## Aktualisieren eines Dienstverweises  
 Das Entity Data Model für einen [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] ändert sich gelegentlich.  Wenn dies geschieht, muss der Dienstverweis aktualisiert werden.  
  
#### So aktualisieren Sie einen Dienstverweis  
  
-   Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Dienstverweis, und klicken Sie dann auf **Dienstverweis aktualisieren**.  
  
     Ein Statusdialogfeld wird angezeigt während der Verweis vom ursprünglichen Speicherort aktualisiert wird. Der Dienstclient wird erneut generiert, um jede Änderung in den Metadaten widerzuspiegeln.  
  
## Entfernen eines Dienstverweises  
 Wenn ein Dienstverweis nicht mehr verwendet wird, können Sie ihn aus der Projektmappe entfernen.  
  
#### So entfernen Sie einen Dienstverweis  
  
-   Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Dienstverweis, und klicken Sie dann auf **Löschen**.  
  
     Der Dienstclient wird aus der Projektmappe entfernt, und die Metadaten, die den Dienst beschreiben, werden aus der Datei **app.config** entfernt.  
  
    > [!NOTE]
    >  Code, der auf den Dienstverweis verweist, muss manuell entfernt werden.  
  
## Siehe auch  
 [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)