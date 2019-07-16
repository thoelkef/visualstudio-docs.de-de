---
title: Erstellen von übergeordneten Containerordnern für Projektmappen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d50800e527c6e79100bf699172f7fc30881b3299
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332733"
---
# <a name="create-parent-container-folders-for-solutions"></a>Erstellen von übergeordneten containerordnern für Projektmappen
In der Quelle Steuerelement-Plug-in-API-Version 1.2 können einen Benutzer ein einziger Stammknoten Quelle-Ziel-Steuerelement für alle Webprojekte in der Projektmappe angeben. Diese einzelne Stamm ist eine Super Unified-Stamm (SUR) aufgerufen.

 In Source Control-Plug-in-API-Version 1.1, wenn der Benutzer eine Projektmappe zur quellcodeverwaltung hinzugefügt wurde der Benutzer aufgefordert, geben Sie ein Steuerelement-Quelle für jedes Webprojekt.

## <a name="new-capability-flags"></a>Neue funktionsflags
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>Neue Funktionen
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE fast immer einen SUR-Ordner erstellt, wenn eine Projektmappe zur quellcodeverwaltung hinzufügen. Insbesondere erfolgt dies in den folgenden Fällen:

- Das Projekt ist ein Datei-Freigabe-Webprojekt.

- Es gibt unterschiedliche Laufwerke für das Projekt und die Projektmappendatei.

- Es gibt andere Freigaben für das Projekt und die Projektmappendatei.

- Getrennt (in einer Projektmappe unter quellcodeverwaltung) wurden Projekte hinzugefügt.

In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], es wird empfohlen, dass der Name für den SUR-Ordner den Namen der Projektmappe ohne Erweiterung identisch sein. In der folgende Tabelle wird das Verhalten in beiden Versionen zusammengefasst.

|Feature|Datenquellen Sie-Steuerelement-Plug-in-API-Version 1.1|Datenquellen Sie-Steuerelement-Plug-in API-Version 1.2|
|-------------| - | - |
|Hinzufügen der Lösung zum SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|
|Projekt der quellcodeverwaltung unterliegende Projektmappe hinzufügen|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **Hinweis**:  Visual Studio wird davon ausgegangen, dass eine Projektmappe direkt untergeordnetes Element von der (Süd).|

## <a name="examples"></a>Beispiele
 Die folgende Tabelle enthält zwei Beispiele. In beiden Fällen die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzer zur Eingabe aufgefordert, einen Zielspeicherort für die Projektmappe unter quellcodeverwaltung, bis die *User_choice* als Ziel angegeben ist. Wenn die User_choice angegeben wird, werden die Projektmappe und zwei Projekte hinzugefügt, ohne Aufforderung des Benutzers für Datenquellen-Steuerelement-Ziele.

|Projektmappe enthält|Auf Datenträger|Datenbank-Standardstruktur|
|-----------------------|-----------------------|--------------------------------|
|*sln1.sln*<br /><br /> Web1<br /><br /> Web2|*C:\Solutions\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot$\Web2|$/ < User_choice > / sln1<br /><br /> $/ < User_choice >/C/Web1<br /><br /> $/ < User_choice > / Web2|
|*sln1.sln*<br /><br /> Web1<br /><br /> Win1|*C:\Solutions\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\solutions\sln1\Win1*|$/ < User_choice > / sln1<br /><br /> $/ < User_choice >/D/web1<br /><br /> $/<user_choice>/sln1/win1|

 Die SUR-Ordner und Unterordner werden erstellt, unabhängig davon, ob der Vorgang abgebrochen wird oder aufgrund eines Fehlers fehlschlägt. Sie werden nicht automatisch in "Abbrechen" oder fehlerbedingungen entfernt.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] standardmäßig auf Version 1.1-Verhalten, wenn das Quellcodeverwaltungs-Plug-in nicht zurückgibt `SCC_CAP_CREATESUBPROJECT` und `SCC_CAP_GETPARENTPROJECT` funktionsflags. Darüber hinaus Benutzern [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] können auch die Version 1.1-Verhalten durch Festlegen des Werts von den folgenden Schlüssel wiederherstellen *DWORD: 00000001*:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateSolutionRootFolderInSourceControl** = *dword:00000001*

## <a name="see-also"></a>Siehe auch
- [Neuerungen in der Quelle Steuerelement-Plug-in-API-Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)