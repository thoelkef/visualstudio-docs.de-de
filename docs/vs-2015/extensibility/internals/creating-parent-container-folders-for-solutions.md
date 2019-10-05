---
title: Erstellen von übergeordneten Containerordnern für Projektmappen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b756da118943dd94bfd3bc5220dfc398c60e2a9e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196928"
---
# <a name="creating-parent-container-folders-for-solutions"></a>Erstellen von übergeordneten Containerordnern für Projektmappen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Source-Plug-in-API Version 1.2 kann einem Benutzer ein einziger Stammknoten Quelle-Ziel-Steuerelement für alle Webprojekte in der Projektmappe angegeben. Diese einzelne Stamm ist eine Super Unified-Stamm (SUR) aufgerufen.  
  
 In der Quelle-Plug-in-API Version 1.1 Wenn der Benutzer eine Projektmappe zur quellcodeverwaltung hinzugefügt wurde der Benutzer aufgefordert, geben Sie ein Steuerelement-Quelle für jedes Webprojekt.  
  
## <a name="new-capability-flags"></a>Neue Funktionsflags  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Neue Funktionen  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE fast immer einen SUR-Ordner erstellt, wenn eine Projektmappe zur quellcodeverwaltung hinzufügen. Insbesondere erfolgt dies in den folgenden Fällen:  
  
- Das Projekt ist eine Dateifreigabe Webprojekt.  
  
- Es gibt unterschiedliche Laufwerke für das Projekt und die Projektmappendatei.  
  
- Es gibt andere Freigaben für das Projekt und die Projektmappendatei.  
  
- Getrennt (in einer Projektmappe unter quellcodeverwaltung) wurden Projekte hinzugefügt.  
  
  In [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] es wird empfohlen, dass der Name für den SUR-Ordner den Namen der Projektmappe ohne Erweiterung identisch sein. In der folgende Tabelle wird das Verhalten in beiden Versionen zusammengefasst.  
  
|Feature|tSource-Steuerelement-Plug-in-API-Version 1.1|Datenquellen Sie-Steuerelement-Plug-in API-Version 1.2|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Hinzufügen der Lösung zum SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Projekt der quellcodeverwaltung unterliegende Projektmappe hinzufügen|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject() **Note:**  Visual Studio wird davon ausgegangen, dass eine Projektmappe direkt untergeordnetes Element von der (Süd).|  
  
## <a name="examples"></a>Beispiele  
 Die folgende Tabelle enthält zwei Beispiele. In beiden Fällen die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Benutzer zur Eingabe aufgefordert, einen Zielspeicherort für die Projektmappe unter quellcodeverwaltung, bis die *User_choice* als Ziel angegeben ist. Wenn die User_choice angegeben wird, werden die Projektmappe und zwei Projekte hinzugefügt, ohne Aufforderung des Benutzers für Datenquellen-Steuerelement-Ziele.  
  
|Projektmappe enthält|Auf Datenträger|Datenbank-Standardstruktur|  
|-----------------------|-----------------------|--------------------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> Web2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot$\web2|$/*User_choice*/sln1<br /><br /> $/*User_choice*  /C/Web1<br /><br /> $/*User_choice*/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*User_choice*/sln1<br /><br /> $/*User_choice*  /D/web1<br /><br /> $/*User_choice*  /sln1/win1|  
  
 Die SUR-Ordner und Unterordner werden erstellt, unabhängig davon, ob der Vorgang wurde abgebrochen oder aufgrund eines Fehlers fehlschlägt. Sie werden nicht automatisch in "Abbrechen" oder fehlerbedingungen entfernt.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] standardmäßig auf Version 1.1-Verhalten, wenn das Quellcodeverwaltungs-Plug-in nicht zurückgibt `SCC_CAP_CREATESUBPROJECT` und `SCC_CAP_GETPARENTPROJECT` funktionsflags. Darüber hinaus Benutzern [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , um die Version 1.1-Verhalten wiederherzustellen, durch den Wert des folgenden Schlüssels auf DWORD: 00000001 festlegen können:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001  
  
## <a name="see-also"></a>Siehe auch  
 [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
