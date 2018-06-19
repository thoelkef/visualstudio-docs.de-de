---
title: 'Vorgehensweise: angeben, welche Dateien mit ClickOnce veröffentlichten | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.File
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, file exclusion
- files, publishing via ClickOnce
ms.assetid: 579c134a-d50f-4e0c-8e05-2a4ff654896a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c59ffc2324f25c42b505505b0dbea9160ef023a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
ms.locfileid: "31561414"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Gewusst wie: Angeben der mit ClickOnce veröffentlichten Dateien
Beim Veröffentlichen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung, alle ohne Code-Dateien im Projekt werden zusammen mit der Anwendung bereitgestellt. In einigen Fällen möglicherweise nicht möchten oder müssen, um bestimmte Dateien zu veröffentlichen, oder Sie möchten bestimmte Dateien basierend auf Bedingungen zu installieren. Visual Studio stellt die Funktionen zum Ausschließen von Dateien, kennzeichnen Dateien als Datendateien oder erforderliche Komponenten und erstellen Sie Gruppen von Dateien für die bedingte Installation bereit.  
  
 Dateien für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung verwaltet werden die **Anwendungsdateien** (Dialogfeld), über die **veröffentlichen** auf der Seite der **Projekt-Designer**.  
  
 Zu Beginn besteht eine einzelne Dateigruppe namens **(erforderlich)**. Sie können zusätzliche Dateigruppen zu erstellen und diese Dateien zuweisen. Sie können nicht geändert werden die **Downloadgruppe** für Dateien, die zum Ausführen der Anwendung erforderlich sind. Z. B. .exe oder die Dateien der Anwendungsverzeichnis als markiert Datendateien zu gehören, müssen die **(erforderlich)** Gruppe.  
  
 Veröffentlichen Sie den Status einer Datei wird mit markiert **(Auto)**. Beispielsweise verfügt die Anwendung .exe Veröffentlichungsstatus **einschließen (Auto)** standardmäßig.  
  
 Dateien mit der **Buildvorgang** -Eigenschaftensatz auf **Content** werden als Anwendungsdateien gekennzeichnet, und wird als Standardeinstellung markiert werden. Sie können einbezogen, ausgeschlossen oder als Datendateien markiert werden. Ausnahmen sind wie folgt aus:  
  
-   Datendateien, z. B. SQL-Datenbank (MDF- und MDB) und XML-Dateien werden standardmäßig als Datendateien gekennzeichnet werden.  
  
-   Verweise auf Assemblys (DLL-Dateien) werden wie folgt festgelegt, wenn Sie den Verweis hinzugefügt haben: Wenn **lokale Kopie** ist **"false"**, er ist standardmäßig als erforderliche Assembly gekennzeichnet (**erforderliche () Auto)**), die muss im GAC vorhanden sein, bevor die Anwendung installiert wird. Wenn **lokale Kopie** ist **"true"**, wird die Assembly standardmäßig als eine Anwendungsassembly markiert (**einschließen (Auto)**) und in den Ordner der Anwendung bei der Installation kopiert werden. Ein COM-Verweis wird angezeigt, der **Anwendungsdateien** Dialogfeld Feld (als ".ocx"-Datei) nur, wenn seine **isoliert** -Eigenschaftensatz auf **"true"**. Standardmäßig wird es enthalten sein.  
  
### <a name="to-add-files-to-the-application-files-dialog-box"></a>Hinzufügen von Dateien zu der Anwendung (Dialogfeld)  
  
1.  Wählen Sie eine Datendatei im **Projektmappen-Explorer**.  
  
2.  Ändern Sie im Fenster Eigenschaften die **Buildvorgang** Eigenschaft, um die **Content** Wert.  
  
### <a name="to-exclude-files-from-clickonce-publishing"></a>Zum Veröffentlichen von ClickOnce-Dateien ausschließen  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Anwendungsdateien** die Schaltfläche, um die **Anwendungsdateien** (Dialogfeld).  
  
4.  In der **Anwendungsdateien** Dialogfeld wählen die Datei, die Sie ausschließen möchten.  
  
5.  In der **Veröffentlichungsstatus** Feld **ausschließen** aus der Dropdown-Liste.  
  
### <a name="to-mark-files-as-data-files"></a>So markieren Sie Dateien als Datendateien  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Anwendungsdateien** die Schaltfläche, um die **Anwendungsdateien** (Dialogfeld).  
  
4.  In der **Anwendungsdateien** Dialogfeld wählen die Datei, die Sie als Daten markieren möchten.  
  
5.  In der **Veröffentlichungsstatus** Feld **Datendatei** aus der Dropdown-Liste.  
  
### <a name="to-mark-files-as-prerequisites"></a>So markieren Sie Dateien als erforderliche Komponenten  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Anwendungsdateien** die Schaltfläche, um die **Anwendungsdateien** (Dialogfeld).  
  
4.  In der **Anwendungsdateien** Dialogfeld wählen die Anwendungsassembly (DLL-Datei), die Sie als erforderliche Komponente markieren möchten. Beachten Sie, dass es für Ihre Anwendung einen Verweis auf die Anwendungsassembly in der Reihenfolge für in der Liste angezeigt werden muss.  
  
5.  In der **Veröffentlichungsstatus** Feld **erforderliche** aus der Dropdown-Liste.  
  
### <a name="to-add-a-new-file-group"></a>So fügen Sie eine neue Dateigruppe hinzu  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Anwendungsdateien** die Schaltfläche, um die **Anwendungsdateien** (Dialogfeld).  
  
4.  In der **Anwendungsdateien** wählen Sie im Dialogfeld die **Gruppe** Feld für eine Datei, die in die neue Gruppe eingeschlossen werden sollen.  
  
    > [!NOTE]
    >  Dateien benötigen die **Buildvorgang** -Eigenschaftensatz auf **Content** vor die Dateinamen in der **Anwendungsdateien** (Dialogfeld).  
  
5.  In der **Downloadgruppe** Feld  **\<neu... >** aus der Dropdown-Liste.  
  
6.  In der **neue Gruppe** (Dialogfeld), geben Sie einen Namen für die Gruppe, und klicken Sie dann auf **OK**.  
  
### <a name="to-add-a-file-to-a-group"></a>So fügen Sie eine Datei zu einer Gruppe hinzu  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Anwendungsdateien** die Schaltfläche, um die **Anwendungsdateien** (Dialogfeld).  
  
4.  In der **Anwendungsdateien** wählen Sie im Dialogfeld die **Gruppe** Feld für eine Datei, die in die neue Gruppe eingeschlossen werden sollen.  
  
5.  In der **Downloadgruppe** Feld, wählen Sie eine Gruppe aus der Dropdown-Liste.  
  
    > [!NOTE]
    >  Sie können nicht geändert werden die **Downloadgruppe** für Dateien, die zum Ausführen der Anwendung erforderlich sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)