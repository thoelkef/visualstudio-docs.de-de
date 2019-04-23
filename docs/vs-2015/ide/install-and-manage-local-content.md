---
title: Installieren und Verwalten von lokalen Inhalten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- hv_manage
helpviewer_keywords:
- changing content installation source [Help Viewer 2.0]
- updating local content [Help Viewer 2.0]
- Help Viewer 2.0, content installation source
- Help Viewer 2.0, updating local content
- Help Viewer 2.0, changing content installation source
- installing local content [Help Viewer 2.0]
- content installation source [Help Viewer 2.0]
- downloading content [Help Viewer 2.0]
- removing local content [Help Viewer 2.0]
- Help Viewer 2.0, removing local content
- Help Viewer 2.0, installing local content
- Help Viewer 2.0, downloading content
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c549beaf58e64d8026b3f6bd39a3b69922d6b7f6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60097413"
---
# <a name="install-and-manage-local-content"></a>Installieren und Verwalten von lokalen Inhalten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Durch Verwendung des Microsoft Help Viewer können Sie den Hilfeinhalt, der auf dem Computer installiert ist, hinzufügen, entfernen, aktualisieren oder verschieben, um ihn an die Softwareanforderungen anzupassen.  
  
 Um Inhalt auf dem lokalen Computer zu verwalten, müssen Sie sich mit einem Konto anmelden, das über Administratorberechtigungen verfügt. Außerdem können Sie möglicherweise keine lokalen Inhalte verwalten, wenn Sie in einer Unternehmensumgebung arbeiten, da diese Entscheidungen möglicherweise von Systemadministratoren für Ihre Organisation getroffen werden. Weitere Informationen finden Sie im [Help Viewer-Administratorhandbuch](../ide/help-viewer-administrator-guide.md).  
  
## <a name="changing-the-content-installation-source"></a>Ändern der Installationsquelle für Inhalte  
 Standardmäßig installiert der Help Viewer Inhalte, indem er einen Microsoft-Onlinedienst als Quelle verwendet. Sie sollten die Inhaltsquelle im Allgemeinen nicht ändern, es sei denn, Sie arbeiten in einer Unternehmensumgebung, für die ein Systemadministrator bereits Inhalte an einem anderen Speicherort installiert hat.  
  
#### <a name="to-change-the-content-installation-source"></a>So ändern Sie die Inhaltsinstallationsquelle  
  
1. Wählen Sie auf der Registerkarte **Inhalt verwalten** das Optionsfeld **Datenträger** aus.  
  
    > [!NOTE]
    >  Die Option **Datenträger** ist nicht verfügbar, wenn der Administrator keine Berechtigungen zum Ändern der Inhaltsinstallationsquelle erteilt hat. Weitere Informationen finden Sie im [Help Viewer-Administratorhandbuch](../ide/help-viewer-administrator-guide.md).  
  
2. Führen Sie einen der folgenden Schritte aus:  
  
    - Geben Sie den Pfad einer MSHA-Datei oder die URL eines Dienstendpunkts ein.  
  
    - Klicken Sie auf die Schaltfläche „Durchsuchen“ (**…**), um zu einer MSHA-Datei zu navigieren.  
  
    - Wählen Sie in der Liste den zuletzt verwendeten Eintrag aus.  
  
## <a name="download-and-install-content-locally"></a>Herunterladen und lokales Installieren von Inhalten  
 Sie können Themen ohne eine Internetverbindung anzeigen, wenn Sie die Inhalte auf dem lokalen Computer herunterladen und installieren.  
  
> [!IMPORTANT]
>  Zum Installieren von Inhalt müssen Sie sich mit einem Konto anmelden, das über Administratorberechtigungen verfügt.  
  
 Wenn die Visual Studio IDE auf eine andere Sprache als Englisch eingestellt ist, können Sie englische Inhalte, lokalisierte Inhalte oder beides installieren. Es werden jedoch keine Inhalte angezeigt, wenn Sie nur die englische Version installieren und im Dialogfeld **Viewer-Optionen** das Kontrollkästchen **Englische Inhalte in alle Navigationsregisterkarten und F1-Anforderungen einbeziehen** deaktivieren.  
  
#### <a name="to-download-and-install-content"></a>So laden Sie den Inhalt herunter und installieren diesen  
  
1. Wählen Sie die Registerkarte **Inhalt verwalten** aus.  
  
2. Wählen Sie in der Inhaltsliste den Link **Hinzufügen** aus, der sich neben dem bzw. neben den hinzufügenden Buch bzw. Büchern befindet, die Sie herunterladen und installieren möchten.  
  
     Das Buch wird der Liste **Ausstehende Änderungen** hinzugefügt, und die geschätzte Größe des Buchs oder der Bücher, die Sie angegeben haben, wird unterhalb dieser Liste angezeigt. Da einige Bücher die gleichen Themen enthalten, kann die gesamte Downloadgröße mehrerer Bücher kleiner sein als das Ergebnis der summierten Größe für alle Bücher, die Sie angeben.  
  
3. Wählen Sie die Schaltfläche **Aktualisieren**.  
  
     Das Buch oder die Bücher, die Sie angegeben haben, werden mit allen Updates für Bücher installiert, die bereits auf dem Computer vorhanden sind. Installationszeiten schwanken, Sie können jedoch den Status auf der Statusleiste anzeigen.  
  
## <a name="removing-local-content"></a>Entfernen der lokalen Inhalte  
 Sie können Speicherplatz sparen, indem Sie unerwünschten Inhalt vom Computer entfernen.  
  
> [!IMPORTANT]
>  Um Inhalte entfernen zu können, müssen Sie über Administratorberechtigungen verfügen.  
  
 Es wird kein Inhalt angezeigt, wenn die Sprache von Visual Studio IDE nicht auf Englisch festgelegt ist, Sie lokalisierte Inhalte entfernen und das Kontrollkästchen **Englische Inhalte in alle Navigationsregisterkarten und F1-Anforderungen einbeziehen** im Dialogfeld **Viewer-Optionen** deaktiviert ist.  
  
#### <a name="to-remove-content"></a>So entfernen Sie Inhalte  
  
1. Wählen Sie die Registerkarte **Inhalt verwalten** aus.  
  
2. Wählen Sie in der Inhaltsliste den Link **Entfernen** aus, der sich neben dem bzw. neben den zu entfernenden Buch bzw. Büchern befindet.  
  
     Das Buch wird der Liste **Ausstehende Änderungen** hinzugefügt.  
  
3. Wählen Sie die Schaltfläche **Aktualisieren**.  
  
     Das Buch oder die Bücher, die Sie angegeben haben, werden vom Computer entfernt.  
  
## <a name="updating-local-content"></a>Aktualisieren des lokalen Inhalts  
 Auf der Statusleiste wird angegeben, wann Updates für den installierten Inhalt verfügbar sind.  
  
> [!IMPORTANT]
>  Wenn Sie Help Viewer verwenden möchten, um automatisch nach Onlineupdates zu suchen, öffnen Sie das Dialogfeld **Viewer-Optionen**, und aktivieren Sie dann das Kontrollkästchen **Online Inhalte abrufen und nach Inhaltupdates suchen**.  
  
#### <a name="to-update-local-content"></a>So aktualisieren Sie lokale Inhalte  
  
- Wählen Sie in der rechten unteren Ecke der Statusleiste den Link **Hier klicken, um den Download jetzt zu starten** aus.  
  
  Die Updatezeiten können variieren, aber Sie können den Aktualisierungsstatus in der Statusleiste anzeigen.  
  
## <a name="moving-local-content"></a>Verschieben von lokalen Inhalten  
 Sie können Speicherplatz sparen, indem Sie installierten Inhalt vom lokalen Computer in eine Netzwerkfreigabe oder in eine andere Partition auf dem lokalen Computer verschieben.  
  
> [!IMPORTANT]
>  Zum Verschieben von Inhalt müssen Sie sich mit einem Konto anmelden, das über Administratorberechtigungen verfügt.  
  
#### <a name="to-move-local-content"></a>So verschieben Sie lokalen Inhalt  
  
1. Wählen Sie auf der Registerkarte **Inhalt verwalten** unter **Lokaler Speicherpfad** die Schaltfläche **Verschieben** aus.  
  
     Das Dialogfeld **Inhalt verschieben** wird geöffnet.  
  
2. Geben Sie im Textfeld **Nach** einen anderen Speicherort für den Inhalt ein, und wählen Sie dann die Schaltfläche **OK** aus.  
  
3. Klicken Sie auf die Schaltfläche **Schließen**, wenn die Inhalte verschoben wurden.  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft Help Viewer](../ide/microsoft-help-viewer.md)
