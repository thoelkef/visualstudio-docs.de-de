---
title: Entwerfen von XML-Befehlstabelle (. VSCT)-Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b7a28e8ea14d27eb96100a4f1f67a875746dc5f6
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499262"
---
# <a name="design-xml-command-table-vsct-files"></a>Entwerfen von XML-Befehlstabellen (VSCT) Befehlsdateien
Ein XML-Befehl-Tabelle (*VSCT*) Datei beschreibt das Layout und die Darstellung der Befehl-Elemente für ein VSPackage. Befehls-Elemente enthalten, Schaltflächen, Kombinationsfelder, Menüs, Symbolleisten und Gruppen von Elementen für Befehl. Dieser Artikel beschreibt die XML-Befehlsdateien für die Tabelle, wie sie Befehl-Elemente und Menüs auswirken und zu deren Erstellung.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Befehle, Menüs, Gruppen und der VSCT-Datei
 Die *VSCT* Dateien Befehlsgruppen, Menüs und Befehle organisiert sind. XML-tags in der *VSCT* Datei dar, die jedes dieser Elemente zusammen mit anderen zugehörigen Elementen wie z. B. Schaltflächen, Befehl Platzierung und Bitmaps.

 Bei der Erstellung eines neuen VSPackages mit der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Paket-Vorlage, die Vorlage generiert ein *VSCT* -Datei mit der erforderlichen Elemente für einen Menübefehl, Toolfenster oder benutzerdefinierten Editor, abhängig von Ihrer Auswahl. Dies *VSCT* Datei kann anschließend geändert werden, um die Anforderungen der ein bestimmtes VSPackage. Beispiele zur Vorgehensweise beim Ändern einer *VSCT* finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).

 Leer, um ein neues zu erstellen, *VSCT* finden Sie unter [Vorgehensweise: Erstellen einer *VSCT* Datei](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Nach der Erstellung, fügen Sie XML-Elemente, Attribute und Werte in die Datei, um das Layout der Befehl-Element zu beschreiben. Eine detaillierte XML-Schema finden Sie unter den [VSCT XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>Unterschiede zwischen CTC und VSCT-Dateien
 Während die Bedeutung der XML-in Tags einem *VSCT* Datei entsprechen diese Tags in der jetzt veralteten *CTC* Dateiformat vor, die ihre Implementierung ist etwas anders:

-   Die neue  **\<"extern" >** Tag ist, in dem Sie anderen verweisen *h* Dateien kompiliert werden, z. B. die Dateien für die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Symbolleiste.

-   Während *VSCT* Unterstützungsdateien für die **/ include** -Anweisung als *CTC* Dateien zu tun, es bietet auch eine neue  **\<Importieren >** Element. Der Unterschied besteht darin, **/ include** bringt in *alle* die Informationen, während  **\<Importieren >** ermöglicht nur die Namen.

-   Während *CTC* Dateien erfordern eine Headerdatei, in dem Sie Ihre Präprozessordirektiven definieren, die er nicht erforderlich, damit *VSCT* Dateien. Ordnen Sie stattdessen die Anweisungen in der Symboltabelle, befindet sich in der  **\<Symbol >** Elemente, die am unteren Rand der *VSCT* Datei.

-   *VSCT* Feature für eine  **\<Annotation >** -Tag, sodass Sie alle Informationen betten Sie zufrieden sind, z. B. Notizen oder auch Bilder.

-   Werte werden als Attribute für das Element gespeichert.

-   Befehlsflags können einzeln gespeichert oder gestapelt werden.  IntelliSense, funktioniert jedoch nicht auf gestapelte Befehlsflags. Weitere Informationen zu Befehlsflags, finden Sie unter den [CommandFlag-Element](../../extensibility/command-flag-element.md).

-   Sie können mehrere Typen, z. B. Split Dropdownlisten, Combos usw. angeben.

-   GUIDs werden nicht überprüft.

-   Jedes Element der Benutzeroberfläche hat eine Zeichenfolge, die den Text darstellt, der dabei angezeigt wird.

-   Das übergeordnete Element ist optional. Wenn nicht angegeben, handelt es sich bei den Wert *Gruppe unbekannt* verwendet wird.

-   Die *Symbol* Argument ist optional.

-   Bitmap-Abschnitt: in diesem Abschnitt wird dem Verhalten in einer *CTC* Datei mit dem Unterschied, dass Sie jetzt einen Dateinamen über Href angeben können, die von, in abgerufen wird der *vsct.exe* Compiler zum Zeitpunkt der Kompilierung.

-   "RESID": Die alte bitmap-Ressource-ID kann verwendet und noch immer funktioniert gleich sein *CTC* Dateien.

-   HRef: Eine neue Methode, die Sie einen Namen für die Bitmapressource angeben kann. Es wird davon ausgegangen, dass alle verwendet werden, damit Sie die verwendete Bereich weglassen können. Der Compiler sucht zuerst für lokale Ressourcen für die Datei wird auf net Freigaben und alle Ressourcen definiert, durch die **/i** wechseln.

-   Tastenzuordnung: Sie müssen nicht mehr an einen Emulator. Wenn Sie angeben, wird der Compiler davon aus, dass der Editor und den Emulator identisch sind.

-   Keychord: Keychord wurde gelöscht. Das neue Format ist *"Key1" "," Mod1 "," Key2 "," Mod2*.  Sie können entweder ein Zeichen, Hexadezimalwert oder VK Konstante angeben.
       
Neuen Compiler *vsct.exe*, kompiliert Sie beide *CTC* und *VSCT* Dateien. Die alte *ctc.exe* Compiler, jedoch nicht erkennen oder Kompilieren *VSCT* Dateien.

Können Sie die *vsct.exe* Compiler das Konvertieren einer vorhandenen *CTO* Eingabedatei in eine *VSCT* Datei. Weitere Informationen finden Sie unter [Vorgehensweise: erstellen eine VSCT-Datei aus einer vorhandenen CTO-Datei](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

## <a name="the-vsct-file-elements"></a>Die Elemente der VSCT-Datei
 Die Befehlstabelle weist die folgende Hierarchie und die folgenden Elemente:

 [CommandTable-Element](../../extensibility/commandtable-element.md): stellt alle Befehle, Menügruppen und Menüs, die das VSPackage zugeordnet.

 [Extern-Element](../../extensibility/extern-element.md): verweist auf externe .h-Dateien, die Sie zusammenführen möchten die *VSCT* Datei.

 [Include-Element](../../extensibility/include-element.md): verweist auf zusätzlichen Header (. h)-Dateien, die Sie zusammen mit kompilieren möchten Ihre *VSCT* Datei. Ein *VSCT* Datei zählen *h* Dateien, die Konstanten an, definieren Befehle, Menügruppen und Menüs, die die IDE oder einem anderen VSPackage bereitstellt.

 [Commands-Element](../../extensibility/commands-element.md): stellt alle der einzelnen Befehle, die ausgeführt werden können. Jeder Befehl verfügt über die folgenden vier untergeordneten Elemente:

 [Menus-Element](../../extensibility/menus-element.md): stellt alle Menüs und Symbolleisten in das VSPackage. Menüs sind Container für Gruppen von Befehlen.

 [Groups-Element](../../extensibility/groups-element.md): alle Gruppen im VSPackage darstellt. Gruppen sind Sammlungen der einzelnen Befehle.

 [Buttons-Element](../../extensibility/buttons-element.md): stellt alle Schaltflächen und Menüelemente im VSPackage. Schaltflächen sind visuellen Steuerelementen, die mit den Befehlen zugeordnet werden können.

 [Bitmaps-Element](../../extensibility/bitmaps-element.md): stellt alle die Bitmaps für alle Schaltflächen im VSPackage. Bitmaps sind Bilder, die neben oder auf die Befehlsschaltflächen, je nach Kontext anzeigen.

 [CommandPlacements-Element](../../extensibility/commandplacements-element.md): Gibt an zusätzlichen Standorten, in denen die einzelnen Befehle in den Menüs Ihres VSPackage positioniert werden soll.

 [VisibilityConstraints-Element](../../extensibility/visibilityconstraints-element.md): Gibt an, und zwar unabhängig davon, ob ein Befehl überhaupt zeigt an, oder nur in bestimmten Kontexten wie z. B. wenn ein bestimmtes Dialogfeld oder Fenster angezeigt wird. Menüs und Befehle, die einen Wert für dieses Element zeigt nur, wenn der angegebene Kontext aktiv ist. Das Standardverhalten ist, um den Befehl jederzeit anzuzeigen.

 [KeyBindings-Element](../../extensibility/keybindings-element.md): Gibt an, alle tastenzuordnungen für die Befehle. D. h. ein oder mehrere Tastenkombinationen, die gedrückt werden müssen, führen Sie den Befehl ein, z. B. **STRG**+**S**.

 [UsedCommands-Element](../../extensibility/usedcommands-element.md): informiert den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung aus, auch wenn der angegebene Befehl durch anderen Code implementiert wird, wenn das aktuelle VSPackage aktiv ist, die befehlsimplementierung enthält.

 [Symbols-Element](../../extensibility/symbols-element.md): enthält die Symbolnamen und die GUID-IDs für alle Ihre Befehle im Paket.

## <a name="vsct-file-design-guidelines"></a>Richtlinien zum Entwerfen von VSCT-Datei
 Erfolgreich Entwurf eine *VSCT* Datei, die folgenden Richtlinien.

-   Befehle können nur in Gruppen befinden, Gruppen platziert werden können, nur in Menüs und Menüs in Gruppen nur platziert werden können. Nur die Menüs werden tatsächlich angezeigt, in der IDE, Gruppen und Befehle nicht.

-   Untermenüs ein Menü können nicht direkt zugewiesen werden, jedoch müssen zugewiesen werden, um eine Gruppe, die wiederum zu einem Menü zugewiesen wird.

-   Befehle, Untermenüs und Gruppen können eine übergeordnete Gruppe oder ein Menü, die mithilfe des übergeordneten Felds ihrer Richtlinie definieren zugewiesen werden.

-   Organisieren eine Befehlstabelle ausschließlich über die übergeordnete Felder in den Richtlinien ist eine wichtige Einschränkung. Die Anweisungen, die Objekte zu definieren, können nur ein übergeordnetes Argument dauern.

-   Wiederverwenden von Befehlen, Gruppen oder Untermenüs erfordert die Verwendung von eine neue Richtlinie erstellen Sie eine neue Instanz des Objekts durch einen eigenen `GUID:ID` Paar.

-   Jede `GUID:ID` -Paar muss eindeutig sein. Wiederverwenden eines Befehls, der z. B. in einem Menü, eine Symbolleiste, oder in einem Kontextmenü platziert wurde, erfolgt durch die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle.

-   Befehle und Untermenüs können auch zu mehreren Gruppen zugewiesen werden, und mehrere Menüs, die mithilfe von Gruppen zugewiesen werden die [Commands-Element](../../extensibility/commands-element.md).

## <a name="vsct-file-notes"></a>Anmerkungen zu dieser VSCT-Datei
 Wenn Sie Änderungen vornehmen einer *VSCT* Datei nach dem Sie sowohl kompilieren Sie ihn und fügen Sie ihn in einer systemeigenen Satelliten-DLL, führen Sie **devenv.exe/Setup /nosetupvstemplates**. Dies erzwingt, dass dies der Fall ist die VSPackage-Ressourcen, die in der experimentellen Registrierung abgelesen werden, und die interne Datenbank, die beschreibt, angegeben [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] neu erstellt werden.

 Während der Entwicklung ist es möglich, dass mehrere VSPackage-Projekte erstellt und in der experimentellen Registrierungsstruktur, die zu verwirrend Überfrachtung in der IDE führen kann registriert werden. Um dieses Problem zu beheben, können Sie die experimentelle Struktur zurücksetzen, um die Standardeinstellungen, entfernen Sie alle registrierten VSPackages und alle Änderungen, die sie der IDE vorgenommen haben, können. Verwenden Sie zum Zurücksetzen der experimentellen Struktur das CreateExpInstance.exe-Tool, das in Visual Studio SDK enthalten ist. Sie finden sie unter:

 *% PROGRAMFILES (x 86) %\Visual Studio\\\<Version > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 Führen Sie das Tool mithilfe des Befehls **CreateExpInstance/Reset**. Denken Sie daran, dass dieses Tool aus der experimentellen Struktur, alle registrierte VSPackages, die normalerweise nicht entfernt mit installierten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Siehe auch
 [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md)