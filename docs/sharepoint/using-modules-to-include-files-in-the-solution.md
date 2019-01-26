---
title: Verwenden von Modulen zum Einfügen von Dateien in der Lösung | Microsoft-Dokumentation
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
ms.openlocfilehash: 7fe8572ea5ac6f2c100d203063dd43b02c78749b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864188"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Verwenden von Modulen zum Einfügen von Dateien in der Projektmappe
  Möglicherweise gibt es Zeiten, wenn Sie Dateien in der SharePoint-Server unabhängig von deren Dateityp, z. B. neue Masterseiten bereitstellen möchten. Zu diesem Zweck können Sie *Module* (nicht zu verwechseln mit [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Codemodule). Module sind Container für Dateien in einer SharePoint-Lösung. Wenn die Lösung bereitgestellt wird, werden die Dateien in das Modul in die angegebenen Ordner auf dem SharePoint-Server kopiert.  
  
## <a name="module-items-and-elements"></a>Modul-Elemente und Elemente
 Um ein Modul zu erstellen, hinzufügen zu einem Projekt durch Auswahl in der **neues Element hinzufügen** Dialogfeld. Ändern Sie dann die *"Elements.xml"* hinzu, um den Namen der Dateien einzubeziehen bereitgestellt, in denen sie auf dem System befinden, und sie auf dem SharePoint-Server kopiert werden sollen, werden soll.  
  
 Hier ist ein Beispiel für die *"Elements.xml"* -Datei für ein Modul:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
    <Module Name="Module1">  
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />  
    </Module>  
</Elements>  
  
```  
  
 Neu erstellte Module enthalten die folgenden Standarddateien:  
  
|Dateiname|Beschreibung|  
|---------------|-----------------|  
|*Elements.xml*|Die Definitionsdatei für das Modul.|  
|*Sample.txt*|Eine Platzhalterdatei, die als ein Beispiel für eine Datei im Modul fungiert.|  
  
 Die *"Elements.xml"* -Datei enthält die folgenden Elemente:  
  
|Elementname|Beschreibung|  
|------------------|-----------------|  
|Elements|Enthält alle Elemente im Modul definiert.|  
|Modul|Module-Element verfügt über ein einzelnes Attribut, *Namen*, gibt, die den Namen des Moduls, im Format `<Module Name="Module1">`.<br /><br /> Beachten Sie, dass Sie den Namen des Moduls ändern (oder den zugehörigen *Ordnername* Eigenschaft), müssen Sie den Namen in den Module-Element manuell aktualisieren.<br /><br /> Wenn Sie ein Unterverzeichnis für die Dateien in den Module-Element angeben [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) wird automatisch eine entsprechende Verzeichnisstruktur für sie erstellt.|  
|Datei|Der File-Element verfügt über zwei Parameter: *Pfad* und *Url*.<br /><br /> -Pfad: Der Name und Speicherort der Datei in der SharePoint-Lösung. Das Format ist, `Path="Module1\Sample.txt"`.<br /><br /> -Url: Der Speicherort, in dem die Datei auf dem SharePoint-Server bereitgestellt wird. Das Format ist, `Url="Module1/Sample.txt"`.<br /><br /> -Typ: Ein optionales Attribut, das über zwei Einstellungen verfügt: *GhostableInLibrary* und *Ghostable*. Das Format ist, `Type="GhostableInLibrary"`. Angeben von *GhostableInLibrary* bedeutet, dass die Datei wird in einer Dokumentbibliothek in SharePoint zusammen mit einem Listenelement zu die Datei steht, wenn es in der Bibliothek hinzugefügt wird hinzugefügt. Angeben von *Ghostable* bewirkt, dass die Datei außerhalb der Dokumentbibliothek in SharePoint hinzugefügt werden.|  
  
 Jede Datei, die Sie bereitstellen möchten, erfordert ein separates `<File>` Elementeintrag in *"Elements.xml"*.  
  
## <a name="see-also"></a>Siehe auch
 [Vorgehensweise: Schließen Sie Dateien mithilfe eines Moduls](../sharepoint/how-to-include-files-by-using-a-module.md)   
 [So wird es gemacht: Bereitstellen einer Datei](http://go.microsoft.com/fwlink/?LinkID=144271)   
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)   
 [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
