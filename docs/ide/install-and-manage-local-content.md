---
title: "Installieren und Verwalten von lokalen Inhalten | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "hv_manage"
helpviewer_keywords: 
  - "Installationsquelle für Inhalte ändern [Help Viewer 2.0]"
  - "Installationsquelle für Inhalte [Help Viewer 2.0]"
  - "Inhalt herunterladen [Help Viewer 2.0]"
  - "Help Viewer 2.0, Installationsquelle für Inhalte ändern"
  - "Help Viewer 2.0, Installationsquelle für Inhalte"
  - "Help Viewer 2.0, Inhalt herunterladen"
  - "Help Viewer 2.0, Lokalen Inhalt installieren"
  - "Help Viewer 2.0, Lokalen Inhalt entfernen"
  - "Help Viewer 2.0, Lokalen Inhalt aktualisieren"
  - "Lokalen Inhalt installieren [Help Viewer 2.0]"
  - "Lokalen Inhalt entfernen [Help Viewer 2.0]"
  - "Lokalen Inhalt aktualisieren [Help Viewer 2.0]"
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
caps.latest.revision: 25
caps.handback.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Installieren und Verwalten von lokalen Inhalten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durch Verwendung des Microsoft Help Viewer können Sie den Hilfeinhalt, der auf dem Computer installiert ist, hinzufügen, entfernen, aktualisieren oder verschieben, um ihn an die Softwareanforderungen anzupassen.  
  
 Um Inhalt auf dem lokalen Computer zu verwalten, müssen Sie sich mit einem Konto anmelden, das über Administratorberechtigungen verfügt.  Außerdem können Sie möglicherweise keine lokalen Inhalte verwalten, wenn Sie in einer Unternehmensumgebung arbeiten, da diese Entscheidungen möglicherweise von Systemadministratoren für Ihre Organisation getroffen werden.  Weitere Informationen finden Sie im [Help Viewer\-Administratorhandbuch](../ide/help-viewer-administrator-guide.md).  
  
## Ändern der Installationsquelle für Inhalte  
 Standardmäßig installiert der Help Viewer Inhalte, indem er einen Microsoft\-Onlinedienst als Quelle verwendet.  Sie sollten die Inhaltsquelle im Allgemeinen nicht ändern, es sei denn, Sie arbeiten in einer Unternehmensumgebung, für die ein Systemadministrator bereits Inhalte an einem anderen Speicherort installiert hat.  
  
#### So ändern Sie die Inhaltsinstallationsquelle  
  
1.  Wählen Sie auf der Registerkarte **Inhalt verwalten** das Optionsfeld **Datenträger** aus.  
  
    > [!NOTE]
    >  Die Option **Datenträger** ist nicht verfügbar, wenn der Administrator keine Berechtigungen zum Ändern der Inhaltsinstallationsquelle erteilt hat.  Weitere Informationen finden Sie im [Help Viewer\-Administratorhandbuch](../ide/help-viewer-administrator-guide.md).  
  
2.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Geben Sie den Pfad einer MSHA\-Datei oder die URL eines Dienstendpunkts ein.  
  
    -   Klicken Sie auf die Schaltfläche "Durchsuchen" \(**…**\), um zu einer MSHA\-Datei zu navigieren.  
  
    -   Wählen Sie in der Liste den zuletzt verwendeten Eintrag aus.  
  
## Herunterladen und lokales Installieren von Inhalten  
 Sie können Themen ohne eine Internetverbindung anzeigen, wenn Sie die Inhalte auf dem lokalen Computer herunterladen und installieren.  
  
> [!IMPORTANT]
>  Zum Installieren von Inhalt müssen Sie sich mit einem Konto anmelden, das über Administratorberechtigungen verfügt.  
  
 Wenn die Visual Studio IDE auf eine andere Sprache als Englisch eingestellt ist, können Sie englische Inhalte, lokalisierte Inhalte oder beides installieren.  Es werden jedoch keine Inhalte angezeigt, wenn Sie nur die englische Version installieren und im Dialogfeld **Viewer\-Optionen** das Kontrollkästchen **Englische Inhalte in alle Navigationsregisterkarten und F1\-Anforderungen einbeziehen** deaktivieren.  
  
#### So laden Sie den Inhalt herunter und installieren diesen  
  
1.  Wählen Sie die Registerkarte **Inhalt verwalten** aus.  
  
2.  Wählen Sie in der Inhaltsliste den Link **Hinzufügen** aus, der sich neben dem bzw. neben den hinzufügenden Buch bzw. Büchern befindet, die Sie herunterladen und installieren möchten.  
  
     Das Buch wird der Liste **Ausstehende Änderungen** hinzugefügt, und die geschätzte Größe des Buchs oder der Bücher, die Sie angegeben haben, wird unterhalb dieser Liste angezeigt.  Da einige Bücher die gleichen Themen enthalten, kann die gesamte Downloadgröße mehrerer Bücher kleiner sein als das Ergebnis der summierten Größe für alle Bücher, die Sie angeben.  
  
3.  Wählen Sie die Schaltfläche **Aktualisieren**.  
  
     Das Buch oder die Bücher, die Sie angegeben haben, werden mit allen Updates für Bücher installiert, die bereits auf dem Computer vorhanden sind.  Installationszeiten schwanken, Sie können jedoch den Status auf der Statusleiste anzeigen.  
  
## Entfernen der lokalen Inhalte  
 Sie können Speicherplatz sparen, indem Sie unerwünschten Inhalt vom Computer entfernen.  
  
> [!IMPORTANT]
>  Um Inhalte entfernen zu können, müssen Sie über Administratorberechtigungen verfügen.  
  
 Es wird kein Inhalt angezeigt, wenn die Sprache von Visual Studio IDE nicht auf Englisch festgelegt ist, Sie lokalisierte Inhalte entfernen und das Kontrollkästchen **Englische Inhalte in alle Navigationsregisterkarten und F1\-Anforderungen einbeziehen** im Dialogfeld **Viewer\-Optionen** deaktiviert ist.  
  
#### So entfernen Sie Inhalte  
  
1.  Wählen Sie die Registerkarte **Inhalt verwalten** aus.  
  
2.  Wählen Sie in der Inhaltsliste den Link **Entfernen** aus, der sich neben dem bzw. neben den zu entfernenden Buch bzw. Büchern befindet.  
  
     Das Buch wird der Liste **Ausstehende Änderungen** hinzugefügt.  
  
3.  Wählen Sie die Schaltfläche **Aktualisieren**.  
  
     Das Buch oder die Bücher, die Sie angegeben haben, werden vom Computer entfernt.  
  
## Aktualisieren des lokalen Inhalts  
 Auf der Statusleiste wird angegeben, wann Updates für den installierten Inhalt verfügbar sind.  
  
> [!IMPORTANT]
>  Wenn Sie Help Viewer verwenden möchten, um automatisch nach Onlineupdates zu suchen, öffnen Sie das Dialogfeld **Viewer\-Optionen**, und aktivieren Sie dann das Kontrollkästchen **Online Inhalte abrufen und nach Inhaltupdates suchen**.  
  
#### So aktualisieren Sie lokale Inhalte  
  
-   Wählen Sie in der rechten unteren Ecke der Statusleiste den Link **Hier klicken, um den Download jetzt zu starten** aus.  
  
 Die Updatezeiten können variieren, aber Sie können den Aktualisierungsstatus in der Statusleiste anzeigen.  
  
## Verschieben von lokalen Inhalten  
 Sie können Speicherplatz sparen, indem Sie installierten Inhalt vom lokalen Computer in eine Netzwerkfreigabe oder in eine andere Partition auf dem lokalen Computer verschieben.  
  
> [!IMPORTANT]
>  Zum Verschieben von Inhalt müssen Sie sich mit einem Konto anmelden, das über Administratorberechtigungen verfügt.  
  
#### So verschieben Sie lokalen Inhalt  
  
1.  Wählen Sie auf der Registerkarte **Inhalt verwalten** unter **Lokaler Speicherpfad** die Schaltfläche **Verschieben** aus.  
  
     Das Dialogfeld **Inhalt verschieben** wird geöffnet.  
  
2.  Geben Sie im Textfeld **Nach** einen anderen Speicherort für den Inhalt ein, und wählen Sie dann die Schaltfläche **OK** aus.  
  
3.  Klicken Sie auf die Schaltfläche **Schließen**, wenn die Inhalte verschoben wurden.  
  
## Siehe auch  
 [Microsoft Help Viewer](../ide/microsoft-help-viewer.md)