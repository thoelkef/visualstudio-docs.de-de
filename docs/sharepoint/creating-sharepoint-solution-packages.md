---
title: Erstellen von SharePoint-Lösungspaketen | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f7afee863d36796bb481f9aca2c24a9ba891ae7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952724"
---
# <a name="create-sharepoint-solution-packages"></a>Erstellen von SharePoint-Lösungspakete
  Mithilfe des Paket-Designers können Sie Bereitstellungspakete erstellen und anpassen. Beispielsweise können Sie SharePoint-Projektelemente und -Funktionen hinzufügen, den IIS-Server zurücksetzen, Funktionsaktivierungsbereiche festlegen und Funktionsabhängigkeiten identifizieren. Der Designer generiert außerdem ein Manifest, eine XML-Datei, die jedes Paket beschreibt.

## <a name="packaging-tools"></a>Tools zum Packen
 Können Sie die **-Paket-Designer** Anpassung des Pakets und das Manifest zu generieren. Sie können SharePoint-Projektelemente einschließen, konfigurieren, ob der Webserver zurückgesetzt werden soll, und den Bereitstellungsservertyp festlegen. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mithilfe des Paket-Designers](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

 Alternativ können Sie die **Paket-Explorer** so ändern Sie die Funktionen und Elemente in der Paketdatei (*.wsp*). Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mithilfe der Paket-Explorer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

 Sie können Visual Studio und MSBuild verwenden, um das Paket zu erstellen (*.wsp*) Dateien, die SharePoint-Lösung bereitstellen. Bei diesem Vorgang werden die für die SharePoint-Bereitstellung benötigten Manifestdateien generiert. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines SharePoint-Lösungspakets mithilfe von MSBuild-Aufgaben](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).

## <a name="package-designer-options"></a>Paket-Designer-Optionen
 Die folgende Tabelle zeigt den Eigenschaften, die Sie in SharePoint-Paketen mit anpassen können die **-Paket-Designer**.

|Eigenschaft des Paket-Designers|Beschreibung der Standardeinstellung|
|-------------------------------|------------------------------------|
|Name|Erforderlich. Der Standardname des Pakets nastaven NA hodnotu *ProjectName*.|
|Webserver zurücksetzen|Dies ist optional. Wählen Sie, wenn den Webserver nach neu gestartet werden soll die *.wsp* Datei auf dem SharePoint-Server installiert ist.|
|Bereitstellungsservertyp|Erforderlich. In der Standardeinstellung ist der Bereich auf ApplicationServer festgelegt.<br /><br /> ApplicationServer: Beschreibt einen Server, der Dienste hostet.<br /><br /> WebFrontEnd: Beschreibt einen Server, der Websites hostet.|
|Elemente in der Lösung|Alle SharePoint-Projektelemente und -Funktionen, die dem Paket hinzugefügt werden können.|
|Elemente in diesem Paket|Dies ist optional. Alle SharePoint-Elemente und -Funktionen, die Sie im Paket bereitstellen möchten.|

## <a name="configure-the-packaging-process"></a>Konfigurieren des Verpackungsprozesses
 Nachdem Sie SharePoint-Projektmappen in Visual Studio entwickelt haben, können Sie anpassen, wie die Projekte gepackt werden.

 Die folgende Tabelle zeigt die zwei MSBuild-Ziele, die Sie verwenden können, um anzupassen wie die *.wsp* Datei erstellt wird.

|Target|Beschreibung|
|------------|-----------------|
|BeforeLayout|Das Ziel, das sofort Aufgaben ausführt, bevor die Dateien in ein Zwischenverzeichnis kopiert werden. Sie können die Dateien vor dem Erstellen einer Paketdatei (*.wsp*).|
|AfterLayout|Das Ziel, das sofort Aufgaben ausführt, nachdem die Dateien in ein Zwischenverzeichnis kopiert wurden.|

 Weitere Informationen [Vorgehensweise: Anpassen ein SharePoint-Lösungspakets mithilfe von MSBuild-Ziele](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).

## <a name="packaging-architecture"></a>Verpackungsarchitektur
 Die folgenden Schritte durchgeführt, bei der Erstellung eines SharePoint-Pakets (*.wsp*) in Visual Studio.

1. Der Funktionen und Pakete werden überprüft, um sicherzustellen, dass die physikalische und semantische Struktur des Pakets richtig ist.

2. Der Funktionen, Projektelemente und Paketdateien im Paket werden aufgelistet. Manifestdateien für Pakete und Funktionen werden umgewandelt, damit alle erforderlichen Informationen für die Bereitstellung und Aktivierung eingeschlossen sind. Die Token werden durch den vollqualifizierten Wert ersetzt.

3. Das anpassbare MSBuild-Ziel BeforeLayout wird ausgeführt. Sie können diesen Schritt, um die Stellen benutzerdefinierten Änderungen für das Paket vor dem Erstellen der *.wsp* Datei erstellt wird.

4. Die aufgelisteten Dateien werden in ein Zwischenverzeichnis kopiert.

5. Das anpassbare MSBuild-Ziel AfterLayout wird ausgeführt. Sie können diesen Schritt, um die Stellen benutzerdefinierten Änderungen für das Paket vor dem Erstellen der *.wsp* Datei erstellt wird.

6. Die Dateien im Zwischenverzeichnis werden hinzugefügt, um die *.wsp* Datei.

## <a name="package-folder-structure"></a>Paketordnerstruktur
 Beim Packen Ihrer SharePoint-Projekts eine *.wsp* Datei wird erstellt, in der *SolutionFolder\bin\\\<BuildConfiguration >* Ordner. Wenn Ihre Lösung im ist z. B. *C:\Visual Studio 2013\projects\listdefinition1 befindet* und die Buildkonfiguration auf Release festgelegt ist die *.wsp* Datei befindet sich im *C:\Visual Studio 2013\ Projects\ListDefinition1\bin\Release*.

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Vorgehensweise: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mithilfe des Paket-Designers](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
- [Vorgehensweise: Erstellen eines SharePoint-Lösungspakets mithilfe von MSBuild-Aufgaben](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Vorgehensweise: Erstellen eines SharePoint-Lösungspakets mithilfe von MSBuild-Aufgaben](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Vorgehensweise: Anpassen eines SharePoint-Lösungspakets mithilfe von MSBuild-Ziele](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)
