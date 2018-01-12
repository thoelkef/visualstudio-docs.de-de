---
title: "Erstellen von SharePoint-Lösungspaketen | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ee3da66dd8e683748198992041bec5a8139cb7e9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="creating-sharepoint-solution-packages"></a>Erstellen von SharePoint-Lösungspaketen
  Mithilfe des Paket-Designers können Sie Bereitstellungspakete erstellen und anpassen. Beispielsweise können Sie SharePoint-Projektelemente und -Funktionen hinzufügen, den IIS-Server zurücksetzen, Funktionsaktivierungsbereiche festlegen und Funktionsabhängigkeiten identifizieren. Der Designer generiert außerdem ein Manifest, eine XML-Datei, die jedes Paket beschreibt.  
  
## <a name="packaging-tools"></a>Tools zum Packen  
 Sie können die **Paket-Designer** auf das Paket anzupassen und das Manifest zu generieren. Sie können SharePoint-Projektelemente einschließen, konfigurieren, ob der Webserver zurückgesetzt werden soll, und den Bereitstellungsservertyp festlegen. Weitere Informationen finden Sie unter [wie: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mithilfe des Paket-Designers](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
 Alternativ können Sie die **Paket-Explorer** so ändern Sie die Funktionen und Elemente in der Paketdatei (.wsp). Weitere Informationen finden Sie unter [wie: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mit dem Paket-Explorer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
 Mithilfe von Visual Studio und MSBuild können Sie Paketdateien (.wsp) erstellen, die für die SharePoint-Lösung bereitgestellt werden sollen. Bei diesem Vorgang werden die für die SharePoint-Bereitstellung benötigten Manifestdateien generiert. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen Sie ein SharePoint-Paket](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b) und [Vorgehensweise: Erstellen eines SharePoint-Lösungspakets von mithilfe von MSBuild-Aufgaben](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).  
  
## <a name="package-designer-options"></a>Optionen des Paket-Designers  
 Die folgende Tabelle zeigt den Eigenschaften, die Sie in SharePoint-Paketen mit anpassen können die **Paket-Designer**.  
  
|Eigenschaft des Paket-Designers|Beschreibung der Standardeinstellung|  
|-------------------------------|------------------------------------|  
|name|Erforderlich. Der Standardname des Pakets wird festgelegt, um *Projektname*.|  
|Webserver zurücksetzen|Dies ist optional. Legen Sie fest, ob der Webserver neu gestartet werden soll, nachdem die WSP-Datei auf dem SharePoint-Server installiert wurde.|  
|Bereitstellungsservertyp|Erforderlich. In der Standardeinstellung ist der Bereich auf ApplicationServer festgelegt.<br /><br /> ApplicationServer: Beschreibt einen Server, der Dienste hostet.<br /><br /> WebFrontEnd: Beschreibt einen Server, der Websites hostet.|  
|Elemente in der Lösung|Alle SharePoint-Projektelemente und -Funktionen, die dem Paket hinzugefügt werden können.|  
|Elemente in diesem Paket|Dies ist optional. Alle SharePoint-Elemente und -Funktionen, die Sie im Paket bereitstellen möchten.|  
  
## <a name="configuring-the-packaging-process"></a>Konfigurieren des Verpackungsprozesses  
 Nachdem Sie SharePoint-Lösungen in Visual Studio entwickelt haben, können Sie anpassen, wie die Projekte gepackt werden.  
  
 In der folgenden Tabelle werden die zwei MSBuild-Ziele gezeigt, mit denen Sie anpassen können, wie die WSP-Datei erstellt wird.  
  
|Ziel|Beschreibung|  
|------------|-----------------|  
|BeforeLayout|Das Ziel, das sofort Aufgaben ausführt, bevor die Dateien in ein Zwischenverzeichnis kopiert werden. Sie können die Dateien vor dem Erstellen einer Paketdatei (.wsp) ändern.|  
|AfterLayout|Das Ziel, das sofort Aufgaben ausführt, nachdem die Dateien in ein Zwischenverzeichnis kopiert wurden.|  
  
 Weitere Informationen [wie: Anpassen eines SharePoint-Lösungspakets mithilfe von MSBuild-Ziele](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).  
  
## <a name="packaging-architecture"></a>Verpackungsarchitektur  
 Die folgenden Schritte werden ausgeführt, wenn Sie in Visual Studio ein SharePoint-Paket (.wsp) erstellen.  
  
1.  Der Funktionen und Pakete werden überprüft, um sicherzustellen, dass die physikalische und semantische Struktur des Pakets richtig ist.  
  
2.  Der Funktionen, Projektelemente und Paketdateien im Paket werden aufgelistet. Manifestdateien für Pakete und Funktionen werden umgewandelt, damit alle erforderlichen Informationen für die Bereitstellung und Aktivierung eingeschlossen sind. Die Token werden durch den vollqualifizierten Wert ersetzt.  
  
3.  Das anpassbare MSBuild-Ziel BeforeLayout wird ausgeführt. Sie können diesen Schritt erstellen, um benutzerdefinierte Änderungen am Paket vorzunehmen, bevor die WSP-Datei erstellt wird.  
  
4.  Die aufgelisteten Dateien werden in ein Zwischenverzeichnis kopiert.  
  
5.  Das anpassbare MSBuild-Ziel AfterLayout wird ausgeführt. Sie können diesen Schritt erstellen, um benutzerdefinierte Änderungen am Paket vorzunehmen, bevor die WSP-Datei erstellt wird.  
  
6.  Die Dateien im Zwischenverzeichnis werden der WSP-Datei hinzugefügt.  
  
## <a name="package-folder-structure"></a>Paketordnerstruktur  
 Wenn Sie das SharePoint-Projekt packen, WSP-Datei wird erstellt in der SolutionFolder\bin\\*BuildConfiguration* Ordner. Angenommen, wenn die Projektmappe in ist *Laufwerk*: \Visual Studio 2013\Projects\ListDefinition1 und die Buildkonfiguration auf Version festgelegt ist, wird die WSP-Datei befindet sich im *Laufwerk*: \Visual Studio 2013\ Projects\ListDefinition1\bin\Release.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [Vorgehensweise: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mithilfe des Paket-Designers](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)   
 [Vorgehensweise: Erstellen eines SharePoint-Pakets](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)   
 [Vorgehensweise: erstellen ein SharePoint-Lösungspakets mithilfe von MSBuild-Aufgaben](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [Vorgehensweise: Anpassen eines SharePoint-Lösungspakets mithilfe von MSBuild-Zielen](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)  
  
  