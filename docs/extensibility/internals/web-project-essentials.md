---
title: Essentials-Webprojekt | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f3d3069d8cc539deeda7c9d44f8d1cbf27e8821
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721672"
---
# <a name="web-project-essentials"></a>Grundlagen von Webprojekten
Webprojekte erstellen Webanwendungen. Sie können ein Webprojekt verwenden, um eine Webanwendung zu erstellen, die über intelligente Webseiten verfügt. Eine intelligente Webseite verfügt über serverseitigen Code, der die Webseite bei Bedarf rendert.

 Mithilfe von herkömmlichen Programmiersprachen, wie z. b. [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] oder [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], können Sie intelligente Webseiten erstellen, um Informationen von einem Benutzer zu erfassen und zu verarbeiten, in einer Datenbank zu speichern usw.

- Das Code Behind-Modell verknüpft abhängige Quell Code Dateien mit Webseiten, die die Dateierweiterung ". aspx" oder ". asmx" aufweisen. Beispielsweise kann "Hello. aspx" die abhängige Quell Code Datei "Hello.aspx.cs" aufweisen.

- Der serverseitige Code, der einer intelligenten Webseite zugeordnet ist, wird in eine ausführbare Datei kompiliert, die sich im Ordner "Website"/bin "" befindet.

- Zusätzliche Quell Code Dateien, z. b. Hilfsklassen, die keiner bestimmten Webseite zugeordnet sind, befinden sich im Ordner Website/App_Code.

  - Ein Website Projekt (WSP) generiert eine ausführbare Datei für jede intelligente Webseite. Aus beliebigen Quell Code Dateien im Ordner/App_Code werden zusätzliche ausführbare Dateien generiert.

  - Ein Webanwendungs Projekt (WAP) erzeugt eine einzelne ausführbare Datei, die den Code für alle intelligenten Webseiten sowie alle Quelldateien im Ordner "/App_Code" kombiniert.

- Die Projektmappendatei für ein Webprojekt befindet sich separat von der Website selbst. Standardmäßig befinden sich Projektmappendateien unter \Documents und Settings \\*YourAccount*\Eigene Dokumente \\ *\<Visual Studio #* # # > \projects \\*yourwebsite*.

  > [!NOTE]
  > Wenn Sie die Projektmappendatei auf der Website aufbewahren möchten, verschieben Sie Sie einfach dorthin, und öffnen Sie Sie erneut.

- Wenn Sie eine Website öffnen, die keine Projektmappendatei in Visual Studio enthält, wird automatisch eine neue Projektmappendatei generiert.

- Webprojekte haben keine Projektdateien. Die Projektinformationen werden in der Projektmappendatei, der Datei "Web. config" und an anderer Stelle gespeichert.

- Durch das Hinzufügen globaler Eigenschaften zu einem Webprojekt wird automatisch eine Speicherdatei im Projektmappen-Ordner des Webprojekts erstellt.

- Eine intelligente Webseite kann mit einer serverseitigen Programmiersprache verknüpft werden, indem die Page-Direktive oder der \<script runat = "Server" > Tag verwendet wird.

- Darüber hinaus können Webseiten über eine beliebige Anzahl von Client seitigen Skript Blöcken verfügen, die in einer beliebigen Skriptsprache geschrieben wurden.

- Ein Website Projekt System wird implementiert, indem Projekt-und Element Vorlagen und die Registrierung für das [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] Projekt hinzugefügt werden.

- Ein WAP-System wird als Projekt Untertyp implementiert, auch als Projekt Konfiguration bezeichnet. Das [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)]-Projekt wird durch den WAP-Untertyp zum Erstellen des WAP-Systems hinzu. Weitere Informationen zu Projekt Untertypen finden Sie unter [Projekt Untertypen](../../extensibility/internals/project-subtypes.md).

- Eine intelligente Webseite kombiniert HTML mit einer serverseitigen Programmiersprache. Die serverseitige Sprache wird als enthaltene Sprache bezeichnet. Um eine enthaltene Sprache zu unterstützen, muss das Webprojekt System die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> Familie von Schnittstellen implementieren.

  - Um die enthaltene Sprache in einem Editor zu unterstützen, muss der HTML-Sprachdienst die Anzeige von enthaltendem Sprachcode in einem enthaltenen Sprachdienst verzögern.

  - Fehler Marker (rote Wellenlinien) sollten immer im primären Puffer des Code-Editors erstellt werden.

## <a name="see-also"></a>Siehe auch
- [Webprojekte](../../extensibility/internals/web-projects.md)