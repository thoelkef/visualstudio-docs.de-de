---
title: 'Gewusst wie: Angeben der Dateien, die von ClickOnce veröffentlicht werden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e0ef4264629e40380f12fb07623bb9274547713c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841112"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Gewusst wie: Angeben der mit ClickOnce veröffentlichten Dateien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Veröffentlichen einer- [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung werden alle nicht-Code Dateien im Projekt zusammen mit der Anwendung bereitgestellt. In einigen Fällen möchten Sie möglicherweise bestimmte Dateien nicht veröffentlichen oder müssen bestimmte Dateien auf der Grundlage von Bedingungen installieren. Visual Studio bietet die Funktionen zum Ausschließen von Dateien, zum Markieren von Dateien als Datendateien oder erforderliche Komponenten und zum Erstellen von Dateigruppen für die bedingte Installation.  
  
 Dateien für eine- [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung werden im Dialogfeld **Anwendungs Dateien** verwaltet, das über die Seite **veröffentlichen** des Projekt- **Designers**zugänglich ist.  
  
 Anfänglich gibt es eine einzelne Datei Gruppe mit dem Namen **(erforderlich)**. Sie können zusätzliche Dateigruppen erstellen und Ihnen Dateien zuweisen. Die **Download Gruppe** kann nicht für Dateien geändert werden, die für die Anwendung erforderlich sind. Beispielsweise müssen die exe-Dateien oder Dateien der Anwendung, die als Datendateien gekennzeichnet sind, zur Gruppe **(erforderlich)** gehören.  
  
 Der Standardwert für den Veröffentlichungsstatus einer Datei wird mit **(Auto)** markiert. Beispielsweise hat die exe-Anwendung (. exe) standardmäßig den Veröffentlichungsstatus **include (Auto)** .  
  
 Dateien, bei **denen die Eigenschaft** Buildvorgang auf **Inhalt** festgelegt ist, werden als Anwendungs Dateien festgelegt und als standardmäßig eingeschlossen gekennzeichnet. Sie können als Datendateien eingeschlossen, ausgeschlossen oder gekennzeichnet werden. Folgende Ausnahmen gelten:  
  
- Datendateien wie SQL-Datenbankdateien (MDF-und MDB-Dateien) und XML-Dateien werden standardmäßig als Datendateien gekennzeichnet.  
  
- Verweise auf Assemblys (DLL-Dateien) werden wie folgt festgelegt, wenn Sie den Verweis hinzufügen: Wenn " **lokal kopieren** " auf " **false**" festgelegt ist, wird es standardmäßig als erforderliche Assembly (erforderliche Komponente **(Voraussetzung (Auto)**) gekennzeichnet, die vor der Installation der Anwendung im GAC vorhanden sein muss Wenn " **lokal kopieren** " auf " **true**" gesetzt ist, wird die Assembly standardmäßig als Anwendungsassembly markiert (**include (Auto)**) und wird bei der Installation in den Anwendungsordner kopiert. Ein COM-Verweis wird nur dann im Dialogfeld **Anwendungs Dateien** (als OCX-Datei) angezeigt, wenn die **isolierte** Eigenschaft auf **true**festgelegt ist. Standardmäßig wird der Wert eingeschlossen.  
  
### <a name="to-add-files-to-the-application-files-dialog-box"></a>So fügen Sie dem Dialog Feld "Anwendungs Dateien" Dateien hinzu  
  
1. Wählen Sie eine Datendatei in **Projektmappen-Explorer**aus.  
  
2. Ändern Sie im Eigenschaftenfenster die Eigenschaft **Buildaktion** in den Wert **Content** .  
  
### <a name="to-exclude-files-from-clickonce-publishing"></a>So schließen Sie Dateien von der ClickOnce-Veröffentlichung aus  
  
1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2. Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3. Klicken Sie auf die Schaltfläche **Anwendungs Dateien** , um das Dialogfeld **Anwendungs Dateien** zu öffnen.  
  
4. Wählen Sie im Dialogfeld **Anwendungs Dateien** die Datei aus, die Sie ausschließen möchten.  
  
5. Wählen Sie im Feld **Veröffentlichungs Status** in der Dropdown Liste die Option **ausschließen** aus.  
  
### <a name="to-mark-files-as-data-files"></a>So markieren Sie Dateien als Datendateien  
  
1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2. Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3. Klicken Sie auf die Schaltfläche **Anwendungs Dateien** , um das Dialogfeld **Anwendungs Dateien** zu öffnen.  
  
4. Wählen Sie im Dialogfeld **Anwendungs Dateien** die Datei aus, die Sie als Daten markieren möchten.  
  
5. Wählen Sie im Feld **Veröffentlichungs Status** in der Dropdown Liste die Option **Datendatei** aus.  
  
### <a name="to-mark-files-as-prerequisites"></a>So markieren Sie Dateien als erforderliche Komponenten  
  
1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2. Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3. Klicken Sie auf die Schaltfläche **Anwendungs Dateien** , um das Dialogfeld **Anwendungs Dateien** zu öffnen.  
  
4. Wählen Sie im Dialogfeld **Anwendungs Dateien** die Anwendungsassembly (DLL-Datei) aus, die Sie als Voraussetzung markieren möchten. Beachten Sie, dass Ihre Anwendung über einen Verweis auf die Anwendungsassembly verfügen muss, damit Sie in der Liste angezeigt wird.  
  
5. Wählen Sie im Feld **Veröffentlichungs Status** in der Dropdown Liste die Option **Voraussetzung** aus.  
  
### <a name="to-add-a-new-file-group"></a>So fügen Sie eine neue Datei Gruppe hinzu  
  
1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2. Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3. Klicken Sie auf die Schaltfläche **Anwendungs Dateien** , um das Dialogfeld **Anwendungs Dateien** zu öffnen.  
  
4. Wählen Sie im Dialogfeld **Anwendungs Dateien** das **Gruppen** Feld für eine Datei aus, die Sie in die neue Gruppe einschließen möchten.  
  
    > [!NOTE]
    > Für Dateien muss die Eigenschaft **Buildaktion** auf **Inhalt** festgelegt sein, bevor die Dateinamen im Dialogfeld **Anwendungs Dateien** angezeigt werden.  
  
5. Wählen Sie im Feld **Gruppe herunterladen** in **\<New...>** der Dropdown Liste aus.  
  
6. Geben Sie im Dialogfeld **neue Gruppe** einen Namen für die Gruppe ein, und klicken Sie dann auf **OK**.  
  
### <a name="to-add-a-file-to-a-group"></a>So fügen Sie einer Gruppe eine Datei hinzu  
  
1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2. Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3. Klicken Sie auf die Schaltfläche **Anwendungs Dateien** , um das Dialogfeld **Anwendungs Dateien** zu öffnen.  
  
4. Wählen Sie im Dialogfeld **Anwendungs Dateien** das **Gruppen** Feld für eine Datei aus, die Sie in die neue Gruppe einschließen möchten.  
  
5. Wählen Sie im Feld **Gruppe herunterladen** eine Gruppe aus der Dropdown Liste aus.  
  
    > [!NOTE]
    > Die **Download Gruppe** kann nicht für Dateien geändert werden, die für die Anwendung erforderlich sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [How to: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
