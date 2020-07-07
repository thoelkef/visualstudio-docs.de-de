---
title: Verwenden von Modulen zum Einschließen von Dateien in die Projekt Mappe | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: overview
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
ms.openlocfilehash: 778bbc9cff2d7853628edbb5be6466acc55d9ab8
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015821"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Verwenden von Modulen zum Einschließen von Dateien in die Projekt Mappe
  Manchmal kann es vorkommen, dass Sie Dateien auf dem SharePoint-Server unabhängig vom Dateityp bereitstellen möchten, z. b. neue Masterseiten. Zu diesem Zweck können Sie *Module* verwenden (nicht zu verwechseln mit [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Code Modulen). Module sind Container für Dateien in einer SharePoint-Lösung. Wenn die Lösung bereitgestellt wird, werden die Dateien im Modul in die angegebenen Ordner auf dem SharePoint-Server kopiert.

## <a name="module-items-and-elements"></a>Modul Elemente und-Elemente
 Um ein Modul zu erstellen, fügen Sie es einem Projekt hinzu, indem Sie es im Dialogfeld **Neues Element hinzufügen** auswählen. Ändern Sie dann die *Elements.xml* Datei so, dass Sie die Namen der Dateien enthält, die Sie bereitstellen möchten, wo Sie sich auf dem System befinden und wo Sie auf den SharePoint-Server kopiert werden sollen.

 Im folgenden finden Sie ein Beispiel für die *Elements.xml* -Datei für ein Modul:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 Neu erstellte Module enthalten die folgenden Standard Dateien:

|Dateiname|BESCHREIBUNG|
|---------------|-----------------|
|*Elements.xml*|Die Definitionsdatei für das Modul.|
|*Sample.txt*|Eine Platzhalter Datei, die als Beispiel für eine Datei im Modul dient.|

 Die *Elements.xml* -Datei enthält die folgenden Elemente:

|Elementname|BESCHREIBUNG|
|------------------|-----------------|
|Elemente|Enthält alle Elemente, die im Modul definiert sind.|
|Modul|Das Module-Element verfügt über ein einzelnes Attribut *namens*, das den Namen des Moduls im-Format angibt `<Module Name="Module1">` .<br /><br /> Beachten Sie, dass Sie den Namen im Modul Element manuell aktualisieren müssen, wenn Sie den Namen des Moduls (oder dessen Eigenschaft *Ordnername* ) ändern.<br /><br /> Wenn Sie ein Unterverzeichnis für die Datei (en) im Modul Element angeben, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] erstellt (WSS) automatisch eine passende Verzeichnisstruktur.|
|File|Das File-Element verfügt über zwei Parameter: *path* und *URL*.<br /><br /> -Path: der Name und Speicherort der Datei in der SharePoint-Lösung. Das Format ist, `Path="Module1\Sample.txt"` .<br /><br /> -URL: der Speicherort, an dem die Datei auf dem SharePoint-Server bereitgestellt wird. Das Format ist, `Url="Module1/Sample.txt"` .<br /><br /> -Type: ein optionales Attribut, das über zwei Einstellungen verfügt: *GhostableInLibrary* und *Ghostable*. Das Format ist, `Type="GhostableInLibrary"` . Das Angeben von *GhostableInLibrary* bedeutet, dass die Datei zu einer Dokumentbibliothek in SharePoint hinzugefügt wird und ein Listenelement hinzugefügt wird, um die Datei zu begleiten, wenn Sie der Bibliothek hinzugefügt wird. Durch das Angeben von *Ghostable* wird die Datei zu SharePoint außerhalb der Dokumentbibliothek hinzugefügt.|

 Für jede Datei, die Sie bereitstellen möchten, ist ein separater `<File>` Element Eintrag in *Elements.xml*erforderlich.

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: einschließen von Dateien mithilfe eines Moduls](../sharepoint/how-to-include-files-by-using-a-module.md)
- [Vorgehensweise: Bereitstellen einer Datei](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
- [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
