---
title: Erstellen von SharePoint-Lösungspaketen | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 957789c4adfc476429179ed84f87f544c0d37143
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765270"
---
# <a name="create-sharepoint-solution-packages"></a>Erstellen von SharePoint-Lösungspaketen
  Mithilfe des Paket-Designers können Sie Bereitstellungspakete erstellen und anpassen. Beispielsweise können Sie SharePoint-Projektelemente und -Funktionen hinzufügen, den IIS-Server zurücksetzen, Funktionsaktivierungsbereiche festlegen und Funktionsabhängigkeiten identifizieren. Der Designer generiert außerdem ein Manifest, eine XML-Datei, die jedes Paket beschreibt.  
  
## <a name="packaging-tools"></a>Tools zum Packen
 Sie können die **Paket-Designer** auf das Paket anzupassen und das Manifest zu generieren. Sie können SharePoint-Projektelemente einschließen, konfigurieren, ob der Webserver zurückgesetzt werden soll, und den Bereitstellungsservertyp festlegen. Weitere Informationen finden Sie unter [wie: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mithilfe des Paket-Designers](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
 Alternativ können Sie die **Paket-Explorer** so ändern Sie die Funktionen und Elemente in der Paketdatei (*WSP*). Weitere Informationen finden Sie unter [wie: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mit dem Paket-Explorer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
 Sie können Visual Studio und MSBuild verwenden, um Paket zu erstellen (*WSP*) Dateien, die SharePoint-Lösung bereitstellen. Bei diesem Vorgang werden die für die SharePoint-Bereitstellung benötigten Manifestdateien generiert. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen Sie ein SharePoint-Paket](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b) und [Vorgehensweise: Erstellen eines SharePoint-Lösungspakets von mithilfe von MSBuild-Aufgaben](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).  
  
## <a name="package-designer-options"></a>Optionen des Paket-Designers
 Die folgende Tabelle zeigt den Eigenschaften, die Sie in SharePoint-Paketen mit anpassen können die **Paket-Designer**.  
  
|Eigenschaft des Paket-Designers|Beschreibung der Standardeinstellung|  
|-------------------------------|------------------------------------|  
|name|Erforderlich. Der Standardname des Pakets wird festgelegt, um *Projektname*.|  
|Webserver zurücksetzen|Dies ist optional. Wählen Sie, wenn der Webserver nach der neu gestartet werden sollen die *WSP* Datei auf dem SharePoint-Server installiert ist.|  
|Bereitstellungsservertyp|Erforderlich. In der Standardeinstellung ist der Bereich auf ApplicationServer festgelegt.<br /><br /> ApplicationServer: Beschreibt einen Server, der Dienste hostet.<br /><br /> WebFrontEnd: Beschreibt einen Server, der Websites hostet.|  
|Elemente in der Lösung|Alle SharePoint-Projektelemente und -Funktionen, die dem Paket hinzugefügt werden können.|  
|Elemente in diesem Paket|Dies ist optional. Alle SharePoint-Elemente und -Funktionen, die Sie im Paket bereitstellen möchten.|  
  
## <a name="configure-the-packaging-process"></a>Konfigurieren des Verpackungsprozesses
 Nachdem Sie SharePoint-Lösungen in Visual Studio entwickelt haben, können Sie anpassen, wie die Projekte gepackt werden.  
  
 Die folgende Tabelle zeigt die zwei MSBuild-Ziele, die Sie verwenden können, um anzupassen wie die *WSP* Datei wird erstellt.  
  
|Ziel|Beschreibung|  
|------------|-----------------|  
|BeforeLayout|Das Ziel, das sofort Aufgaben ausführt, bevor die Dateien in ein Zwischenverzeichnis kopiert werden. Ändern Sie die Dateien vor dem Erstellen einer Paketdatei (*WSP*).|  
|AfterLayout|Das Ziel, das sofort Aufgaben ausführt, nachdem die Dateien in ein Zwischenverzeichnis kopiert wurden.|  
  
 Weitere Informationen [wie: Anpassen eines SharePoint-Lösungspakets mithilfe von MSBuild-Ziele](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).  
  
## <a name="packaging-architecture"></a>Verpackungsarchitektur
 Die folgenden Schritte durchgeführt werden, wenn Sie ein SharePoint-Paket erstellen (*WSP*) in Visual Studio.  
  
1.  Der Funktionen und Pakete werden überprüft, um sicherzustellen, dass die physikalische und semantische Struktur des Pakets richtig ist.  
  
2.  Der Funktionen, Projektelemente und Paketdateien im Paket werden aufgelistet. Manifestdateien für Pakete und Funktionen werden umgewandelt, damit alle erforderlichen Informationen für die Bereitstellung und Aktivierung eingeschlossen sind. Die Token werden durch den vollqualifizierten Wert ersetzt.  
  
3.  Das anpassbare MSBuild-Ziel BeforeLayout wird ausgeführt. Sie können diesen Schritt, um stellen eine beliebige benutzerdefinierte Änderungen am Paket vor dem Erstellen der *WSP* Datei wird erstellt.  
  
4.  Die aufgelisteten Dateien werden in ein Zwischenverzeichnis kopiert.  
  
5.  Das anpassbare MSBuild-Ziel AfterLayout wird ausgeführt. Sie können diesen Schritt, um stellen eine beliebige benutzerdefinierte Änderungen am Paket vor dem Erstellen der *WSP* Datei wird erstellt.  
  
6.  Die Dateien im Zwischenverzeichnis werden hinzugefügt, auf die *WSP* Datei.  
  
## <a name="package-folder-structure"></a>Paketordnerstruktur
 Wenn Sie das SharePoint-Projekt, Verpacken einer *WSP* Datei wird erstellt, in der *SolutionFolder\bin\{BuildConfiguration}* Ordner. Angenommen, wenn die Projektmappe in ist *C:\Visual Studio 2013\Projects\ListDefinition1* und die Buildkonfiguration auf Version festgelegt ist die *WSP* Datei befindet sich im *C:\Visual Studio 2013\ Projects\ListDefinition1\bin\Release*.  
  
## <a name="see-also"></a>Siehe auch
 [Vorgehensweise: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [Vorgehensweise: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mithilfe des Paket-Designers](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)   
 [Vorgehensweise: Erstellen eines SharePoint-Pakets](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)   
 [Vorgehensweise: erstellen ein SharePoint-Lösungspakets mithilfe von MSBuild-Aufgaben](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [Vorgehensweise: Anpassen eines SharePoint-Lösungspakets mithilfe von MSBuild-Zielen](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)  
  
 