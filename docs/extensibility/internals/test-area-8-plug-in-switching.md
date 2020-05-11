---
title: 'Testbereich 8: Plug-in-Umschaltung | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 799fb04936a24004d73ce4c8aa3ec654490f3f62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704393"
---
# <a name="test-area-8-plug-in-switching"></a>Testbereich 8: Plug-In-Wechsel
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE) verfügt über die Benutzeroberfläche (UI), um das aktuelle Quellcodeverwaltungs-Plug-In zu ändern. Dieser Testbereich bietet Testfälle für den Prozess der Kommissionierung, welches Plug-In für die Lösungsquellcodekontrolle verwendet werden soll.

## <a name="command-menu-access"></a>Befehlsmenüzugriff
 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] den Testfällen werden die folgenden integrierten Menüpfade für Entwicklungsumgebungen verwendet.

- Aktuelles Quellcodeverwaltungs-Plug-In: **Tools** -> **Options** -> **Source Control** -> **Plug-in Selection**.

- Quellcodeverwaltungsbindung ändern: -> **Dateiquellcodeverwaltung** -> **Änderung Quellcodeverwaltung**... **File**

## <a name="common-expected-behavior"></a>Häufiges erwartetes Verhalten
 Das Ändern des Quellcodeverwaltungs-Plug-Ins für eine Lösung ist möglich, ohne Visual Studio zu beenden oder die Lösung neu zu laden. Darüber hinaus ändert sich das aktuelle Quellcodeverwaltungs-Plug-In automatisch in das Plug-In, das von einer Lösung verwendet wird, wenn diese Lösung geladen wird.

## <a name="test-cases"></a>Testfälle
 Im Folgenden finden Sie spezifische Testfälle für den Plug-in-Switching-Testbereich.

### <a name="case-8a-automatic-change"></a>Fall 8a: Automatischer Wechsel

#### <a name="expected-behavior"></a>Erwartetes Verhalten
 Wenn ein Benutzer eine Lösung lädt, die sich unter Quellcodeverwaltung befindet, wird die Lösung automatisch geladen, und das entsprechende Quellcodeverwaltungs-Plug-In wird als Strom ausgewählt.

| Aktion | Testschritte | Erwartete Ergebnisse zur Überprüfung |
| - | - | - |
| Automatischer Quellcodeverwaltungs-Plug-In-Wechsel | 1. Wählen Sie das unter Test prüfende Plug-In als aktuell aus (**Tools** -> **Options** -> Source Control**Plug-in****Source Control** -> Selection .)<br />2. Erstellen Sie ein neues Projekt.<br />3. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />4. Wählen Sie ein anderes [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]Plug-In (z. B. ).<br />5. Akzeptieren Sie die Lösungsaufforderung.<br />6. Öffnen Sie die Lösung erneut von der Festplatte aus. | Die Lösung wird geöffnet.<br /><br /> Plug-in im Test ist das aktuelle Quellcodeverwaltungs-Plug-In. |

### <a name="case-8b-solution-based-change"></a>Fall 8b: Lösungsbasierter Wandel

#### <a name="expected-behavior"></a>Erwartetes Verhalten
 Die Lösung kann das zugehörige Quellcodeverwaltungs-Plug-In ändern.

| Aktion | Testschritte | Erwartete Ergebnisse zur Überprüfung |
|----------------------------------| - | - |
| Wechsel des Plug-Ins für eine Lösung | 1. Wählen Sie das unter Test befindliche Plug-In als aktuell aus (**Tools** -> **Options** -> Source Control**Plug-in****Source Control** -> Selection ).<br />2. Erstellen Sie ein neues Projekt und eine neue Projektmappe.<br />3. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />4. Entbinden Sie die Solution von der Quellcodeverwaltung (mit dem Dialogfeld **Quellcodeverwaltung ändern).**<br />5. Wählen Sie ein anderes [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]Plug-In (z. B. ).<br />6. Laden Sie die Lösung nach dem Entladen vom Datenträger neu.<br />7. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />8. Entbinden Sie die Solution von der Quellcodeverwaltung (mit Dialogfeld **Quellcodeverwaltung ändern).**<br />9. Wählen Sie das unter Test erneut eiserne Plug-In erneut aus.<br />10. Laden Sie die Lösung nach dem Entladen vom Datenträger neu.<br />11. Binden Sie die Lösung an den ursprünglichen Speicherort (mit dem Dialogfeld **Quellcodeverwaltung ändern).** | Die Lösung wird der Quellcodeverwaltung mithilfe des ausgewählten Plug-Ins hinzugefügt. |

## <a name="see-also"></a>Weitere Informationen
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
