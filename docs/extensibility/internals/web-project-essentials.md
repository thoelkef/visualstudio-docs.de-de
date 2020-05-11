---
title: Web-Projekt Grundlagen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09e33248ca264fefa79a8d5d5fa5d0cfa3d2da1d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703552"
---
# <a name="web-project-essentials"></a>Grundlagen von Webprojekten
Webprojekte erstellen Webanwendungen. Sie können ein Webprojekt verwenden, um eine Webanwendung mit intelligenten Webseiten zu erstellen. Eine intelligente Webseite verfügt über serverseitigen Code, der die Webseite bei Bedarf rendert.

 Mithilfe herkömmlicher Programmiersprachen, z. [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] B. oder [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], können Sie intelligente Webseiten erstellen, um Informationen von einem Benutzer zu sammeln und zu verarbeiten, sie in einer Datenbank zu speichern usw.

- Das CodeBehind-Modell ordnet abhängige Quellcodedateien Webseiten zu, die die Dateierweiterung .aspx oder .asmx haben. Beispielsweise kann hello.aspx die abhängige Quellcodedatei hello.aspx.cs haben.

- Der serverseitige Code, der einer intelligenten Webseite zugeordnet ist, wird in eine ausführbare Datei kompiliert, die sich im Ordner Website /bin befindet.

- Zusätzliche Quellcodedateien, z. B. Hilfsklassen, die keiner bestimmten Webseite zugeordnet sind, befinden sich im Ordner Website/App_Code.

  - Ein Websiteprojekt (WSP) generiert eine ausführbare Datei für jede intelligente Webseite. Zusätzliche ausführbare Dateien werden aus allen Quellcodedateien im Ordner /App_Code generiert.

  - Ein Webanwendungsprojekt (WAP) erstellt eine einzelne ausführbare Datei, die den Code für alle intelligenten Webseiten sowie alle Quelldateien im Ordner /App_Code kombiniert.

- Die Projektmappendatei für ein Webprojekt befindet sich getrennt von der Website selbst. In der Standardeinstellung befinden sich Lösungsdateien unter "Dokumente und\\Einstellungen*YourAccount"*\\*\<(Dokumente" Visual Studio, >*. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .*YourWebSite*\\

  > [!NOTE]
  > Wenn Sie die Lösungsdatei mit der Website beibehalten möchten, verschieben Sie sie einfach dorthin, und öffnen Sie sie erneut.

- Wenn Sie eine Website öffnen, die keine Projektmappendatei in Visual Studio enthält, wird automatisch eine neue Projektmappendatei für sie generiert.

- Webprojekte haben keine Projektdateien. Projektinformationen werden in der Projektmappendatei, der Datei web.config und an anderer Stelle gespeichert.

- Durch das Hinzufügen globaler Eigenschaften zu einem Webprojekt wird automatisch eine Speicherdatei im Ordner "Webprojektmappen" erstellt.

- Eine intelligente Webseite kann einer serverseitigen Programmiersprache zugeordnet werden, \<indem die Page-Direktive oder das Skript runat="server">-Tag verwendet wird.

- Darüber hinaus können Webseiten eine beliebige Anzahl von clientseitigen Skriptblöcken in einer beliebigen Skriptsprache geschrieben haben.

- Ein Websiteprojektsystem wird durch Hinzufügen von Projekt- und [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] Elementvorlagen und Registrierung zum Projekt implementiert.

- Ein WAP-System wird als Projektuntertyp implementiert, der auch als Projektgeschmack bezeichnet wird. Das [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] Projekt wird vom WAP-Subtyp geschmeckt, um das WAP-System zu erstellen. Weitere Informationen zu Projektuntertypen finden Sie unter [Projektuntertypen](../../extensibility/internals/project-subtypes.md).

- Eine intelligente Webseite kombiniert HTML mit einer serverseitigen Programmiersprache. Die serverseitige Sprache wird als enthaltene Sprache bezeichnet. Um eine enthaltene Sprache zu unterstützen, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> muss das Webprojektsystem die Familie der Schnittstellen implementieren.

  - Um die enthaltene Sprache in einem Editor zu unterstützen, muss der HTML-Sprachdienst die Anzeige von enthaltenem Sprachcode auf einen enthaltenen Sprachdienst verschieben.

  - Fehlermarkierungen (rote Squigglies) sollten immer im primären Puffer des Codeeditors erstellt werden.

## <a name="see-also"></a>Weitere Informationen
- [Webprojekte](../../extensibility/internals/web-projects.md)
