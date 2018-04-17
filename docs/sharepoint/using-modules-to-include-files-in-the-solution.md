---
title: Verwenden von Modulen zum Einfügen von Dateien in die Projektmappe | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9c11dd4ebd17b1ebef91c3d7752df7c15dd50da4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="using-modules-to-include-files-in-the-solution"></a>Verwenden von Modulen zum Einfügen von Dateien in die Projektmappe
  Möglicherweise gibt es Zeiten, wenn Sie Dateien auf dem SharePoint-Server unabhängig von deren Dateityp, z. B. neue Gestaltungsvorlagen bereitstellen möchten. Zu diesem Zweck können Sie *Module* (nicht zu verwechseln mit [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Codemodule). Module sind Container für Dateien in einer SharePoint-Lösung. Wenn die Lösung bereitgestellt wird, werden die Dateien in das Modul für die angegebenen Ordner auf dem SharePoint-Server kopiert.  
  
## <a name="module-items-and-elements"></a>Modul und Elemente  
 Um ein Modul erstellen, fügen sie zu einem Projekt durch Auswahl in der **neues Element hinzufügen** (Dialogfeld). Anschließend ändern Sie die Datei "Elements.xml", um die Namen der Dateien aufzunehmen, die Sie bereitstellen möchten, in denen sie auf dem System befinden, und sie auf dem SharePoint-Server kopiert werden soll, ein.  
  
 Hier ist ein Beispiel der Datei "Elements.xml" für ein Modul:  
  
```  
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
|Elements.xml|Die Definitionsdatei für das Modul.|  
|"Sample.txt"|Ein Platzhalterdatei, die als ein Beispiel für eine Datei in das Modul fungiert.|  
  
 Die Datei "Elements.xml" enthält die folgenden Elemente:  
  
|Elementname|Beschreibung|  
|------------------|-----------------|  
|Elements|Enthält alle Elemente, die im Modul definiert.|  
|Modul|Module-Element verfügt über ein einzelnes Attribut *Namen*, gibt, die den Namen des Moduls im Format `<Module Name="Module1">`.<br /><br /> Beachten Sie, dass, wenn Sie den Namen des Moduls ändern (oder den zugehörigen *Ordnername* Eigenschaft), müssen Sie den Namen im Module-Element manuell aktualisieren.<br /><br /> Wenn Sie ein Unterverzeichnis für die Dateien in den Module-Element angeben [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) wird automatisch eine entsprechende Verzeichnisstruktur für sie erstellt.|  
|Datei|Der File-Element verfügt über zwei Parameter *Pfad* und *Url*.<br /><br /> -Path: Der Name und Speicherort der Datei in der SharePoint-Lösung. Das Format ist, `Path="Module1\Sample.txt"`.<br /><br /> -Url: Der Speicherort, in dem die Datei auf dem SharePoint-Server bereitgestellt wird. Das Format ist, `Url="Module1/Sample.txt"`.<br /><br /> -Typ: Ein optionales Attribut, das zwei Einstellungen aufweist: *GhostableInLibrary* und *Ghostable*. Das Format ist, `Type="GhostableInLibrary"`. Angeben von *GhostableInLibrary* bedeutet, dass die Datei wird in einer Dokumentbibliothek in SharePoint zusammen mit einem Listenelement zu die Datei steht, wenn sie in der Bibliothek hinzugefügt wird hinzugefügt werden. Angeben von *Ghostable* bewirkt, dass die Datei in SharePoint außerhalb der Dokumentbibliothek hinzugefügt werden.|  
  
 Jede Datei, die Sie bereitstellen möchten, erfordert eine Separate `<File>` Element Eintrag in der Datei "Elements.xml".  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Einschließen von Dateien mithilfe eines Moduls](../sharepoint/how-to-include-files-by-using-a-module.md)   
 [Vorgehensweise: Bereitstellen eine Datei](http://go.microsoft.com/fwlink/?LinkID=144271)   
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)   
 [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Verpacken und Bereitstellen von SharePoint-Projektmappen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  