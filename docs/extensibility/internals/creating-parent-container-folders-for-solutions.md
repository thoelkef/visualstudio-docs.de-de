---
title: "Erstellen von übergeordneten Container und Ordner für Lösungen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ea901fe4e380fd867db1c63e44bc1cb6e144feb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="creating-parent-container-folders-for-solutions"></a>Erstellen von übergeordneten Container und Ordner für Projektmappen
In der Quelle Steuerelement-Plug-in-API Version 1.2 kann Benutzer ein einziger Stammknoten Quelle Steuerelement Ziel für alle Web-Projekte innerhalb der Projektmappe angeben. Diese einzelstamm wird eine Super Unified Stamm (SUR) bezeichnet.  
  
 In der Quelle Steuerelement-Plug-in-API Version 1.1 Wenn der Benutzer eine Projektmappe zur quellcodeverwaltung, hinzugefügt wurde der Benutzer aufgefordert, ein Datenquellen-Steuerelement-Ziel für jedes Webprojekt anzugeben.  
  
## <a name="new-capability-flags"></a>Neue Funktion Flags  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Neue Funktionen  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE fast immer einen Ordner "SUR" erstellt, wenn eine Projektmappe zur quellcodeverwaltung hinzufügen. Insbesondere geschieht dies in den folgenden Fällen:  
  
-   Das Projekt ist eine Dateifreigabe Webprojekt.  
  
-   Es gibt verschiedene Laufwerke für das Projekt und die Projektmappendatei.  
  
-   Es gibt andere Freigaben für das Projekt und die Projektmappendatei.  
  
-   Projekte, die separat (in einer Projektmappe unter quellcodeverwaltung) hinzugefügt wurden.  
  
 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wird vorgeschlagen, dass der Name des Ordners SUR identisch mit den Namen der Projektmappe ohne Erweiterung. In der folgenden Tabelle wird das Verhalten in beiden Versionen zusammengefasst.  
  
|Funktion|tSource Steuerelement-Plug-in-API-Version 1.1|Quellcodeverwaltung-Plug-in-API-Version 1.2|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Hinzufügen von Projektmappen mit Quellcodeverwaltung|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Projekt Projektmappe unter quellcodeverwaltung hinzufügen|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject() **Hinweis:** Visual Studio wird davon ausgegangen, dass ein direkt untergeordnetes Element von der sur funktioniert|  
  
## <a name="examples"></a>Beispiele  
 Die folgende Tabelle enthält zwei Beispiele. In beiden Fällen die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzer wird aufgefordert, für einen Zielspeicherort für die Projektmappe unter quellcodeverwaltung, bis die *User_choice* als Ziel angegeben ist. Wenn die User_choice angegeben wird, werden die Projektmappe und zwei Projekte hinzugefügt, ohne eine benutzeraufforderung Source Control Ziele.  
  
|Projektmappe enthält|Auf dem Datenträger|Datenbank-Standardstruktur|  
|-----------------------|-----------------------|--------------------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> WEB2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot$\web2|$/*User_choice*/sln1<br /><br /> $/*User_choice*  /C/Web1<br /><br /> $/*User_choice*/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*User_choice*/sln1<br /><br /> $/*User_choice*  /D/web1<br /><br /> $/*User_choice*  /sln1/win1|  
  
 Die SUR-Ordner und Unterordner werden erstellt, unabhängig davon, ob der Vorgang abgebrochen wird oder aufgrund eines Fehlers fehlschlägt. Sie werden nicht automatisch in "Abbrechen" oder fehlerbedingungen entfernt.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]standardmäßig auf Version 1.1-Verhalten, wenn die Datenquellen-Steuerelement-Plug-in nicht zurückgibt `SCC_CAP_CREATESUBPROJECT` und `SCC_CAP_GETPARENTPROJECT` Funktion Flags. Darüber hinaus Benutzern [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] können, um das Verhalten der Version 1.1 wiederherzustellen, indem Sie den Wert des folgenden Schlüssels auf DWORD: 00000001 auswählen:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001  
  
## <a name="see-also"></a>Siehe auch  
 [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)