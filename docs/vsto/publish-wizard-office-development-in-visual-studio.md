---
title: Veröffentlichungsassistent (Office-Entwicklung in Visual Studio)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2481557d1d75d64b5eb3f52f2755953ca344d323
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692719"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Veröffentlichungsassistent (Office-Entwicklung in Visual Studio)
  Verwenden der **Veröffentlichungs-Assistenten** um Projektmappendateien an einem bestimmten Speicherort zu kopieren, Erstellen der Manifestdateien, und ein Setupprogramm erstellen.  
  
 Mit diesem Assistenten für den Zugriff auf die **erstellen** Menü wählen **veröffentlichen** *SolutionName*. Sie können auch Zugriff auf die **Veröffentlichungs-Assistenten** aus **Projektmappen-Explorer**. Öffnen Sie das Kontextmenü für den Projektknoten, und wählen Sie dann **veröffentlichen**.  
  
 Jeder Abschnitt weiter unten wird eine Seite des Assistenten beschrieben.  
  
## <a name="where-do-you-want-to-publish-the-application"></a>Wo möchten Sie die Anwendung veröffentlichen?  
 **Geben Sie den Speicherort aus, um diese Anwendung zu veröffentlichen.**  
 Erforderlich. Ort der Veröffentlichung ist das Verzeichnis, in dem die **Veröffentlichungs-Assistenten** kopiert die Projektmappendateien, z. B. Manifeste, Assemblys, temporäre Zertifikate und andere Dateien aus dem Build. Sie benötigen Schreibzugriff auf dieses Verzeichnis.  
  
 Geben Sie den Speicherort als Datenträgerpfad, Dateifreigabe, FTP-Site oder URL der Website, oder klicken Sie auf die **Durchsuchen** Schaltfläche, um den Speicherort zu navigieren. Der Pfad kann in diesen Formaten sein:  
  
-   Ein relativer oder absoluter Pfad im Standard Windows format, z. B. *C:\Deploy\MyApplication* oder *\MyApplication*.  
  
-   Einen Pfad (UNC = Universal Naming Convention) wie z. B.  *\\\ServerName\MyApplication\\*.  
  
-   Eine URL einer Website, z. B. http://www.microsoft.com/MyApplication.  
  
 Speicherort für die Veröffentlichung ist standardmäßig *http://localhost/projectname/* Wenn auf dem IIS installiert, oder das Verzeichnis publish, wenn Sie dies tun müssen IIS nicht installiert.  
  
> [!NOTE]  
>  Es sind weitere Aspekte auf, wenn der Zielcomputer Windows Vista ausgeführt wird. Sie müssen Administrator auf dem Windows Vista-Computer mit der Option "lokale veröffentlichen" sein. Darüber hinaus ist der Standardspeicherort immer die *veröffentlichen\\*  Verzeichnis, unabhängig davon, ob IIS installiert ist.  
  
## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Was ist der Standardinstallationspfad auf Endbenutzercomputern vorhanden?  
 Der Installationspfad ist optional. Sie können den Installationspfad später festlegen, falls gewünscht. Weitere Informationen finden Sie unter [Vorgehensweise: Ändern des Installationspfads einer Office-Projektmappe](http://msdn.microsoft.com/en-us/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
 Der Installationspfad ist das Verzeichnis, über das der Endbenutzer die Anpassung installiert. Hierbei handelt es sich ebenfalls um den Pfad, der von der Projektmappe für die Suche nach Updates verwendet wird. Die **Veröffentlichungs-Assistenten** wird nicht an diesem Speicherort die Projektmappe bereitgestellt, es sei denn, der Pfad identisch, mit der Sie eingegeben, in haben der **Geben Sie den Speicherort aus, um diese Anwendung veröffentlichen** Feld auf der vorherigen Seite.  
  
 **Von einer Website**  
 Geben Sie die URL, die Endbenutzer folgen, um die Projektmappe installiert wird.  
  
 **Von einem UNC-Pfad oder die Dateifreigabe**  
 Geben Sie den UNC-Pfad, den Endbenutzer folgen, um die Projektmappe installiert wird.  
  
 **Von einer CD-ROM oder DVD-ROM**  
 Diese Option erfordert keinen Installationspfad aus.  
  
 Visual Studio ist nicht die CD oder DVD zu brennen. Sie müssen die Ausgabe mit einer CD oder DVD manuell kopieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen einer Office-Projektmappe mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Veröffentlichungsseite, Projekt-Designer &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)  
  
  