---
title: Veröffentlichungsassistent (Office-Entwicklung in Visual Studio)
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.PublishWizard
- VST.PublishWizard.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], Publish Wizard
- deploying applications [Office development in Visual Studio], Publish Wizard
- Office applications [Office development in Visual Studio], Publish Wizard
- Publish Wizard, Office solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7879ad7cf18c3d09fddbab3923296e0896688af9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447066"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Veröffentlichungsassistent (Office-Entwicklung in Visual Studio)
  Verwenden der **Veröffentlichungs-Assistenten** um Projektmappendateien an einen bestimmten Speicherort zu kopieren, Erstellen der Manifestdateien sowie ein Setupprogramm erstellen.

 Mit diesem Assistenten für den Zugriff auf die **erstellen** Menü wählen **veröffentlichen** *SolutionName*. Sie können auch Zugriff auf die **Veröffentlichungs-Assistenten** aus **Projektmappen-Explorer**. Öffnen Sie das Kontextmenü für den Projektknoten, und wählen Sie dann **veröffentlichen**.

 Einzelnen Abschnitten unten wird eine Seite des Assistenten beschrieben.

## <a name="where-do-you-want-to-publish-the-application"></a>Wo möchten Sie die Anwendung veröffentlichen?
 **Geben Sie den Speicherort zum Veröffentlichen dieser Anwendung** erforderlich sind. Ort der Veröffentlichung wird das Verzeichnis, in denen die **Veröffentlichungs-Assistenten** kopiert die Projektmappendateien, z. B. die Manifeste, Assemblys, temporäre Zertifikate und andere Dateien aus dem Build. Sie benötigen Schreibzugriff auf dieses Verzeichnis.

 Geben Sie den Speicherort als Datenträgerpfad, Dateifreigaben, FTP-Site oder Website-URL ein, oder klicken Sie auf die **Durchsuchen** Schaltfläche, um den Speicherort zu suchen. Der Pfad kann in diesen Formaten sein:

- Ein relativer oder absoluter Pfad im Standard Windows format, z. B. *C:\Deploy\MyApplication* oder *\MyApplication*.

- Ein Universal Naming Convention (UNC)-Pfad, z. B.  *\\\ServerName\MyApplication\\*.

- Eine URL einer Web site, z. B. http://www.microsoft.com/MyApplication.

  Standardmäßig ist der Ort der Veröffentlichung *http://localhost/projectname/* Wenn IIS installiert, oder das Verzeichnis "publish\" verwendet, wenn Sie dies tun nicht IIS installiert haben.

> [!NOTE]
> Es sind weitere Überlegungen, wenn es sich bei dem Ziel-PC Windows Vista ausgeführt wird. Sie müssen ein Administrator auf dem Windows Vista-Computer mit der Option für lokale Veröffentlichung sein. Darüber hinaus ist der Standardspeicherort immer das *veröffentlichen\\*  Verzeichnis, unabhängig davon, ob IIS installiert ist.

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Was ist der Standardpfad für die Installation auf Computern von Endbenutzern?
 Der Installationspfad ist optional. Sie können den Installationspfad später festlegen, falls gewünscht. Weitere Informationen finden Sie unter [Vorgehensweise: Ändern des Installationspfads einer Office-Projektmappe](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).

 Der Installationspfad ist das Verzeichnis, aus dem der Endbenutzer die Anpassung installiert. Hierbei handelt es sich ebenfalls um den Pfad, der von der Projektmappe für die Suche nach Updates verwendet wird. Die **Veröffentlichungs-Assistenten** wird nicht an diesem Speicherort, die Lösung bereitgestellt, es sei denn, der Pfad identisch mit der Sie eingegeben, in haben der **Geben Sie den Speicherort zum Veröffentlichen dieser Anwendung** Feld auf der vorherigen Seite.

 **Von einer Website** Geben Sie die URL, die Endbenutzer folgen werden, um die Lösung installieren.

 **Von einem UNC-Pfad oder Dateifreigabe** Geben Sie den UNC-Pfad, die Endbenutzer folgen werden, um die Lösung installieren.

 **Von einer CD-ROM oder DVD-ROM-** diese Option erfordert keinen Installationspfad aus.

 Visual Studio ist nicht auf der CD oder DVD brennen. Sie müssen die Ausgabe auf eine CD oder DVD manuell kopieren.

## <a name="see-also"></a>Siehe auch
- [Bereitstellen einer Office-Projektmappe mit ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Veröffentlichungsseite, Projekt-Designer &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)
