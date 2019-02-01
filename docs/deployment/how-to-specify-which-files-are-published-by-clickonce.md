---
title: 'Vorgehensweise: Angeben der mit ClickOnce veröffentlichten Dateien | Microsoft-Dokumentation'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b24cb2b90bdd9e3fad5128a483314d75ffc1672f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54926883"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Vorgehensweise: Angeben der mit ClickOnce veröffentlichten Dateien
Beim Veröffentlichen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung, alle nicht-Code-Dateien im Projekt zusammen mit der Anwendung bereitgestellt werden. In einigen Fällen möglicherweise nicht möchten oder müssen bestimmte Dateien zu veröffentlichen, oder möchten Sie möglicherweise bestimmte Dateien, die basierend auf Bedingungen zu installieren. Visual Studio bietet die Funktionen zum Ausschließen von Dateien, kennzeichnen von Dateien als Datendateien oder erforderliche Komponenten und Erstellen von Dateigruppen zur bedingten Installation.  
  
 Dateien für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung verwaltet werden, der **Anwendungsdateien** klicken Sie im Dialogfeld aus zugegriffen werden kann die **veröffentlichen** auf der Seite die **Projekt-Designer**.  
  
 Es ist zunächst eine einzelne Dateigruppe mit dem Namen **(erforderlich)**. Sie können weitere Dateigruppen erstellen und Dateien zuweisen. Sie können nicht geändert werden die **Downloadgruppe** für Dateien, die für die Ausführung der Anwendung erforderlich sind. Z. B. die oder der Anwendung .exe-Dateien als markiert Datendateien zu gehören, müssen die **(erforderlich)** Gruppe.  
  
 Veröffentlichen Sie den Status einer Datei wird mit markiert **(Auto)**. Beispielsweise weist der Anwendung .exe Veröffentlichungsstatus **einschließen (Auto)** standardmäßig.  
  
 Dateien mit der **Buildvorgang** -Eigenschaftensatz auf **Content** werden als Dateien der Anwendung bestimmt und wird als Standardeinstellung markiert. Sie können enthalten, ausgeschlossen oder als Datendateien markiert werden. Die Ausnahmen sind wie folgt aus:  
  
-   Datendateien wie SQL-Datenbank (*mdf* und *MDB*) und XML-Dateien werden als Datendateien standardmäßig gekennzeichnet werden.  
  
-   Verweise auf Assemblys (*DLL* Dateien) werden wie folgt gekennzeichnet, wenn Sie den Verweis hinzufügen: Wenn **lokale Kopie** ist **"false"**, er ist standardmäßig als erforderliche Assembly gekennzeichnet (**Voraussetzung (Auto)**), die muss im GAC vorhanden sein, bevor die Anwendung installiert wird. Wenn **lokale Kopie** ist **"true"**, die Assembly ist standardmäßig als eine Anwendungsassembly gekennzeichnet (**einschließen (Auto)**) und in den Ordner der Anwendung, bei der Installation kopiert werden. Ein COM-Verweis wird angezeigt, der **Anwendungsdateien** im Dialogfeld (als ein *OCX* Datei) nur, wenn die **isoliert** -Eigenschaftensatz auf **"true"**. Standardmäßig werden sie berücksichtigt.  
  
### <a name="to-add-files-to-the-application-files-dialog-box"></a>Das Dialogfeld "Anwendungsdateien" Dateien hinzufügen  
  
1.  Wählen Sie eine Datei im **Projektmappen-Explorer**.  
  
2.  Ändern Sie im Fenster Eigenschaften die **Buildvorgang** Eigenschaft, um die **Content** Wert.  
  
### <a name="to-exclude-files-from-clickonce-publishing"></a>So schließen Sie Dateien von ClickOnce-Veröffentlichung  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf die **Anwendungsdateien** die Schaltfläche, um die **Anwendungsdateien** Dialogfeld.  
  
4.  In der **Anwendungsdateien** Dialogfeld Feld, wählen Sie die Datei, die Sie ausschließen möchten.  
  
5.  In der **Veröffentlichungsstatus** die Option **ausschließen** aus der Dropdown-Liste.  
  
### <a name="to-mark-files-as-data-files"></a>So markieren Sie die Dateien als Datendateien  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf die **Anwendungsdateien** die Schaltfläche, um die **Anwendungsdateien** Dialogfeld.  
  
4.  In der **Anwendungsdateien** Dialogfeld Feld, wählen Sie die Datei, die Sie als Daten markieren möchten.  
  
5.  In der **Veröffentlichungsstatus** die Option **Datendatei** aus der Dropdown-Liste.  
  
### <a name="to-mark-files-as-prerequisites"></a>Dateien als erforderliche Komponente aktivieren  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf die **Anwendungsdateien** die Schaltfläche, um die **Anwendungsdateien** Dialogfeld.  
  
4.  In der **Anwendungsdateien** Dialogfeld wählen die Assembly (*DLL* Datei), die Sie als erforderliche Komponente markieren möchten. Beachten Sie, dass Ihre Anwendung einen Verweis auf die Anwendungsassembly in der Reihenfolge, in der Liste angezeigt.  
  
5.  In der **Veröffentlichungsstatus** die Option **erforderliche** aus der Dropdown-Liste.  
  
### <a name="to-add-a-new-file-group"></a>Eine neue Dateigruppe hinzufügen  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf die **Anwendungsdateien** die Schaltfläche, um die **Anwendungsdateien** Dialogfeld.  
  
4.  In der **Anwendungsdateien** wählen Sie im Dialogfeld die **Gruppe** Feld für eine Datei, die Sie in der neuen Gruppe einschließen möchten.  
  
    > [!NOTE]
    >  Dateien müssen die **Buildvorgang** -Eigenschaftensatz auf **Content** vor den Dateinamen in angezeigt werden die **Anwendungsdateien** im Dialogfeld.  
  
5.  In der **Downloadgruppe** die Option  **\<neu... >** aus der Dropdown-Liste.  
  
6.  In der **neue Gruppe** Dialogfeld Geben Sie einen Namen für die Gruppe, und klicken Sie dann auf **OK**.  
  
### <a name="to-add-a-file-to-a-group"></a>Um eine Datei zu einer Gruppe hinzuzufügen.  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf die **Anwendungsdateien** die Schaltfläche, um die **Anwendungsdateien** Dialogfeld.  
  
4.  In der **Anwendungsdateien** wählen Sie im Dialogfeld die **Gruppe** Feld für eine Datei, die Sie in der neuen Gruppe einschließen möchten.  
  
5.  In der **Downloadgruppe** Feld, wählen Sie eine Gruppe aus der Dropdown-Liste.  
  
    > [!NOTE]
    >  Sie können nicht geändert werden die **Downloadgruppe** für Dateien, die für die Ausführung der Anwendung erforderlich sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Vorgehensweise: Publish a ClickOnce Application using the Publish Wizard (Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten)](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)