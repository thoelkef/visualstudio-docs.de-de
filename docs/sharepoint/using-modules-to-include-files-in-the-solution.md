---
title: Verwenden von Modulen zum Einschließen von Dateien in die Projekt Mappe | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f8f2aa6c5d86af2424a811b6167829cefdb6fb5
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985292"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Verwenden von Modulen zum Einschließen von Dateien in die Projekt Mappe
  Manchmal kann es vorkommen, dass Sie Dateien auf dem SharePoint-Server unabhängig vom Dateityp bereitstellen möchten, z. b. neue Masterseiten. Zu diesem Zweck können Sie *Module* verwenden (nicht zu verwechseln mit [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Code Modulen). Module sind Container für Dateien in einer SharePoint-Lösung. Wenn die Lösung bereitgestellt wird, werden die Dateien im Modul in die angegebenen Ordner auf dem SharePoint-Server kopiert.

## <a name="module-items-and-elements"></a>Modul Elemente und-Elemente
 Um ein Modul zu erstellen, fügen Sie es einem Projekt hinzu, indem Sie es im Dialogfeld **Neues Element hinzufügen** auswählen. Ändern Sie dann die Datei " *Elements. XML* " so, dass Sie die Namen der Dateien enthält, die Sie bereitstellen möchten, wo Sie sich auf dem System befinden und wo Sie auf den SharePoint-Server kopiert werden sollen.

 Im folgenden finden Sie ein Beispiel für die Datei " *Elements. XML* " für ein Modul:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 Neu erstellte Module enthalten die folgenden Standard Dateien:

|Dateiname|Beschreibung|
|---------------|-----------------|
|*"Elements. xml"*|Die Definitionsdatei für das Modul.|
|*Sample. txt*|Eine Platzhalter Datei, die als Beispiel für eine Datei im Modul dient.|

 Die Datei " *Elements. XML* " enthält die folgenden Elemente:

|Elementname|Beschreibung|
|------------------|-----------------|
|Elements|Enthält alle Elemente, die im Modul definiert sind.|
|Modul|Das Module-Element verfügt über ein einzelnes Attribut *namens*, das den Namen des Moduls im Format `<Module Name="Module1">`angibt.<br /><br /> Beachten Sie, dass Sie den Namen im Modul Element manuell aktualisieren müssen, wenn Sie den Namen des Moduls (oder dessen Eigenschaft *Ordnername* ) ändern.<br /><br /> Wenn Sie ein Unterverzeichnis für die Datei (en) im Module-Element angeben, erstellt [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) automatisch eine passende Verzeichnisstruktur.|
|Datei|Das File-Element verfügt über zwei Parameter: *path* und *URL*.<br /><br /> -Path: der Name und Speicherort der Datei in der SharePoint-Lösung. Das Format ist, `Path="Module1\Sample.txt"`.<br /><br /> -URL: der Speicherort, an dem die Datei auf dem SharePoint-Server bereitgestellt wird. Das Format ist, `Url="Module1/Sample.txt"`.<br /><br /> -Type: ein optionales Attribut, das über zwei Einstellungen verfügt: *GhostableInLibrary* und *Ghostable*. Das Format ist, `Type="GhostableInLibrary"`. Das Angeben von *GhostableInLibrary* bedeutet, dass die Datei zu einer Dokumentbibliothek in SharePoint hinzugefügt wird und ein Listenelement hinzugefügt wird, um die Datei zu begleiten, wenn Sie der Bibliothek hinzugefügt wird. Durch das Angeben von *Ghostable* wird die Datei zu SharePoint außerhalb der Dokumentbibliothek hinzugefügt.|

 Jede Datei, die Sie bereitstellen möchten, erfordert einen separaten `<File>` Element-Eintrag in der Datei " *Elements. XML*".

## <a name="see-also"></a>Siehe auch
- [Gewusst wie: einschließen von Dateien mithilfe eines Moduls](../sharepoint/how-to-include-files-by-using-a-module.md)
- [Vorgehensweise: Bereitstellen einer Datei](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
- [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
