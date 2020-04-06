---
title: Erstellen übergeordneter Containerordner für Lösungen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e5481e20a12fc05ccba97eef55173e5ce9b30d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709104"
---
# <a name="create-parent-container-folders-for-solutions"></a>Erstellen übergeordneter Containerordner für Lösungen
In der Quellcodeverwaltungs-Plug-In-API Version 1.2 kann ein Benutzer ein einzelnes Stammquellsteuerungsziel für alle Webprojekte innerhalb der Projektmappe angeben. Dieser einzelne Stamm wird Super Unified Root (SUR) genannt.

 Wenn der Benutzer in der Quellcodeverwaltungs-Plug-In-API Version 1.1 der Quellcodeverwaltung eine Multiprojektlösung hinzugefügt hat, wurde der Benutzer aufgefordert, für jedes Webprojekt ein Quellcodeverwaltungsziel anzugeben.

## <a name="new-capability-flags"></a>Neue Funktionsflags
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>Neue Funktionen
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE erstellt fast immer einen SUR-Ordner, wenn eine Lösung zur Quellcodeverwaltung hinzugefügt wird. Insbesondere in den folgenden Fällen:

- Das Projekt ist ein Webprojekt für Dateifreigaben.

- Es gibt verschiedene Laufwerke für das Projekt und die Projektmappendatei.

- Es gibt verschiedene Freigaben für das Projekt und die Projektmappendatei.

- Projekte wurden separat hinzugefügt (in einer von der Quelle gesteuerten Lösung).

In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]wird vorgeschlagen, dass der Name für den SUR-Ordner mit dem Lösungsnamen ohne die Erweiterung identisch ist. Die folgende Tabelle fasst das Verhalten in den beiden Versionen zusammen.

|Funktion|Quellcodeverwaltung Plug-In-API Version 1.1|Quellcodeverwaltung Plug-In-API Version 1.2|
|-------------| - | - |
|Hinzufügen einer Lösung zu SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|
|Hinzufügen eines Projekts zur lösungunter Quellcodeverwaltung|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **Hinweis:**  Visual Studio geht davon aus, dass eine Lösung ein direktes untergeordnetes Element des SUR ist.|

## <a name="examples"></a>Beispiele
 In der folgenden Tabelle sind zwei Beispiele aufgeführt. In beiden Fällen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wird der Benutzer aufgefordert, einen Zielspeicherort für die Lösung unter Quellcodeverwaltung einzufinden, bis die *user_choice* als Ziel angegeben ist. Wenn die user_choice angegeben ist, werden die Projektmappe und zwei Projekte hinzugefügt, ohne den Benutzer zu Quellcodeverwaltungszielen aufzufordert.

|Lösung enthält|Auf Festplattenstandorten|Datenbankstandardstruktur|
|-----------------------|-----------------------|--------------------------------|
|*sln1.sln*<br /><br /> Web1<br /><br /> Web2|*C:-Lösungen-Sln1*<br /><br /> *C:'Inetpub'wwwroot'Web1*<br /><br /> \\"Server" (Server)|nr./<user_choice>/sln1<br /><br /> nr./<user_choice>/C/Web1<br /><br /> <user_choice>/Web2|
|*sln1.sln*<br /><br /> Web1<br /><br /> Win1|*C:-Lösungen-Sln1*<br /><br /> *D:'Inetpub'wwwroot'Web1*<br /><br /> *C:-Lösungen-Sln1-Win1*|nr./<user_choice>/sln1<br /><br /> nr./<user_choice>/D/web1<br /><br /> nr./<user_choice>/sln1/win1|

 Der SUR-Ordner und die Unterordner werden unabhängig davon erstellt, ob der Vorgang abgebrochen wird oder aufgrund eines Fehlers fehlschlägt. Sie werden nicht automatisch in Abbruch- oder Fehlerbedingungen entfernt.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Standardmäßig auf Version 1.1-Verhalten, wenn das Quellcodeverwaltungs-Plug-In keine Leistungs- und `SCC_CAP_CREATESUBPROJECT` `SCC_CAP_GETPARENTPROJECT` Funktionsflags zurückgibt. Darüber hinaus [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] können Benutzer von wählen, auf das Verhalten version 1.1 zurückzufinden, indem sie den Wert des folgenden Schlüssels auf *dword:00000001*festlegen:

 **[HKEY_CURRENT_USER-Software-, Microsoft-VisualStudio-8.0-SourceControl] DoNotCreateSolutionRootFolderInSourceControl** = *dword:00000001*

## <a name="see-also"></a>Weitere Informationen
- [Neuerungen in der Quellcodeverwaltungs-Plug-In-API Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
