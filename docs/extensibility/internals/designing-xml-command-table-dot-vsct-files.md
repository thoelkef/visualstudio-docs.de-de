---
title: XML-Befehlstabelle entwerfen (. VSCT)-Dateien | Microsoft Docs
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
ms.openlocfilehash: 865baa3f7b4b0fe4cbbaf2cdf34e9e8041d5c121
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133358"
---
# <a name="designing-xml-command-table-vsct-files"></a>XML-Befehlstabelle entwerfen (. VSCT)-Dateien
Eine XML-Tabelle (VSCT) Befehlsdatei beschreibt das Layout und die Darstellung der Elemente der Befehl für ein VSPackage. Befehl Elementen zählen Schaltflächen, Kombinationsfelder, Menüs, Symbolleisten und Elementgruppen Befehl. Dieses Thema beschreibt die XML-Befehlsdateien für die Tabelle, wie sie Befehl und Menüs auswirken und zu deren Erstellung.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Befehle, Menüs, Gruppen und der VSCT-Datei
 VSCT-Dateien sind Befehle, Menüs und Befehlsgruppen organisiert. Darstellen von XML-Tags in der VSCT-Datei jedes dieser Elemente, sowie andere zugehörige Elemente wie z. B. Befehlsschaltflächen Befehl Platzierung und Bitmaps.

 Wenn Sie ein neues VSPackage erstellen, durch Ausführen der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Paketvorlage, die Vorlage generiert eine VSCT-Datei mit der erforderlichen Elemente für einen Menübefehl, Toolfenster oder benutzerdefinierten Editor, abhängig von Ihrer Auswahl. Diese VSCT-Datei kann dann entsprechend den Anforderungen eines bestimmten VSPackage geändert werden. Weitere Beispiele zum Ändern einer VSCT-Datei finden Sie unter den Beispielen in [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).

 Um ein neues, leeres VSCT-Datei zu erstellen, finden Sie unter [Vorgehensweise: Erstellen einer. VSCT-Datei](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Nach der Erstellung, fügen Sie XML-Elemente, Attribute und Werte zu der Datei, die der Befehl das Elementlayout beschreiben. Eine detaillierte XML-Schema finden Sie unter der [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>Unterschiede zwischen CTC und VSCT-Dateien
 Während die Bedeutung der XML-Tags in einer VSCT-Datei identisch sind als diejenigen, die jetzt CTC-Dateiformat veraltet, ist ihre Implementierung geringfügig.

-   Die neue  **\<"extern" >** Tag ist, in dem Sie andere h-Dateien kompiliert werden, etwa solche für verweisen die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Symbolleiste.

-   Während der VSCT-Unterstützungsdateien der **/ include** -Anweisung, wie CTC-Dateien, es bietet zudem eine neue \< **Importieren >** Element. Der Unterschied besteht darin, **/ include** bringt in **alle** Informationstypen, aber \< **Importieren >** ermöglicht nur die Namen.

-   Während der CTC-Dateien eine Headerdatei benötigen, in der Sie Ihre Präprozessordirektiven definieren, muss eine nicht für VSCT-Dateien. Platzieren Sie stattdessen die Anweisungen in der Symboltabelle befindet sich in der  **\<Symbol >** Elemente, die am unteren Rand der VSCT-Datei.

-   VSCT-Dateien-Funktion eine  **\<Annotation >** Tags, das Ihnen die Möglichkeit, alle Informationen einbetten, z. B. Notizen oder auch Bilder möchten.

-   Werte werden als Attribute für das Element gespeichert.

-   Befehlsflags können einzeln gespeichert oder gestapelt werden.  IntelliSense, funktioniert jedoch nicht auf gestapelte Befehlsflags. Weitere Informationen zu Befehlsflags, finden Sie unter der [Flags Befehlselement](../../extensibility/command-flag-element.md).

-   Sie können mehrere Typen, z. B. Split Dropdownlisten, Tastenkürzel usw. angeben.

-   GUIDs werden nicht überprüft.

-   Jedes Element der Benutzeroberfläche hat eine Zeichenfolge, die den Text darstellt, der mit ihm angezeigt wird.

-   Übergeordnete Element ist optional. Wenn nicht angegeben, wird der Wert "Gruppe Unknown" verwendet.

-   Das Symbol "-Argument ist optional.

-   Die Bitmap-Abschnitt--identisch mit einer CTC-Datei, mit dem Unterschied, dass Sie jetzt einen Dateinamen über Href angeben können, die vom Compiler vsct.exe zum Zeitpunkt der Kompilierung herausgezogen werden.

-   ResID--die alte Bitmap-Ressourcen-ID kann verwendet werden und weiterhin funktioniert genauso wie in der CTC-Dateien.

-   HRef – eine neue Methode, die Ihnen ermöglicht, einen Dateinamen für die Bitmapressource angeben. Es wird vorausgesetzt, dass alle verwendet werden, damit Sie die verwendete Bereich weglassen können. Der Compiler sucht zuerst nach lokalen Ressourcen für die Datei, klicken Sie dann auf net Freigaben, und alle Ressourcen, die durch die/i-Switch definiert.

-   KeyBinding – Sie müssen nicht mehr geben Sie einen Emulator aus. Wenn Sie angeben, wird der Compiler davon ausgegangen, dass der Editor und den Emulator identisch sind.

-   Keychord--wurde gelöscht. Das neue Format wird Key1, Mod1, Key2, Mod2.  Sie können Zeichen, hexadezimalen oder VK Konstante angeben.

 Der neue Compiler, vsct.exe, CTC und VSCT-Dateien kompiliert. Der alte ctc.exe Compiler jedoch weder erkannt noch VSCT-Dateien zu kompilieren.

 Den Compiler vsct.exe können Sie um eine vorhandenen CTO-Datei in eine VSCT-Datei zu konvertieren. Weitere Informationen hierzu finden Sie unter [Vorgehensweise: Erstellen einer. VSCT-Datei aus einer vorhandenen. CTO-Datei](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

## <a name="the-vsct-file-elements"></a>Die Elemente der VSCT-Datei
 Die Befehlstabelle weist die folgenden Hierarchie und die folgenden Elemente:

 [CommandTable Element](../../extensibility/commandtable-element.md) – stellt alle Befehle, Menügruppen und Menüs, die das VSPackage zugeordnet.

 [Element "extern"](../../extensibility/extern-element.md) – verweist auf externe h-Dateien, die mit der VSCT-Datei zusammengeführt werden sollen.

 [Include-Element](../../extensibility/include-element.md) – verweist auf zusätzlicher Headerdateien (. h) zusammen mit your.vsct-Datei kompiliert werden sollen. Eine VSCT-Datei zählen h-Dateien, enthält die Konstanten an, die definieren Befehle, Menügruppen und Menüs, die den IDE- oder einem anderen VSPackage bereitstellt.

 [Befehle Element](../../extensibility/commands-element.md) – stellt alle von der einzelnen Befehle, die ausgeführt werden können. Jeder Befehl verfügt über die folgenden vier untergeordneten Elemente:

 [Menüs Element](../../extensibility/menus-element.md) – alle Menüs und Symbolleisten im VSPackage darstellt. Menüs sind Container für Gruppen von Befehlen.

 [Element für Gruppen](../../extensibility/groups-element.md) – alle Gruppen im VSPackage darstellt. Gruppen sind Sammlungen der einzelnen Befehle.

 [Schaltflächen Element](../../extensibility/buttons-element.md) – alle Schaltflächen und Menüelementen im VSPackage darstellt. Schaltflächen sind visuelle Steuerelemente, die Befehle zugeordnet werden können.

 [Bitmaps Element](../../extensibility/bitmaps-element.md) – stellt alle die Bitmaps für alle Schaltflächen im VSPackage. Bitmaps sind Bilder, die neben oder auf die Befehlsschaltflächen, je nach Kontext angezeigt.

 [CommandPlacements Element](../../extensibility/commandplacements-element.md) – gibt an, dass zusätzliche Standorte, in dem die einzelnen Befehle in den Menüs Ihres VSPackage positioniert werden soll.

 [VisibilityConstraints Element](../../extensibility/visibilityconstraints-element.md) – gibt an, und zwar unabhängig davon, ob ein Befehl zeigt überhaupt Zeiten oder nur in bestimmten Kontexten, z. B. bei einem bestimmten Dialogfeld oder Fenster angezeigt wird. Menüs und Befehle, die keinen für dieses Element Wert zeigt nur, wenn der angegebene Kontext aktiv ist. Das Standardverhalten besteht, um den Befehl jederzeit anzuzeigen.

 [Schlüsselbindungen Element](../../extensibility/keybindings-element.md) – gibt alle schlüsselbindungen für die Befehle an. D. h. ein oder mehrere-Tastenkombinationen, die gedrückt werden müssen, führen Sie den Befehl ein, z. B. **STRG + S**.

 [UsedCommands Element](../../extensibility/usedcommands-element.md) – Informs der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ab, obwohl es sich bei der angegebene Befehl durch anderen Code implementiert wird, wenn das aktuelle VSPackage aktiv ist, die Befehl Implementierung bereitstellt.

 `Symbols Element` – Enthält die Symbolnamen und die GUID-IDs für alle Befehle im Paket.

## <a name="vsct-file-design-guidelines"></a>. Richtlinien zum Entwerfen von VSCT-Datei
 Befolgen Sie diese Richtlinien, um eine VSCT-Datei erfolgreich zu entwerfen.

-   Befehle können nur in Gruppen platziert werden, nur in Menüs in Gruppen platziert werden können und Menüs in Gruppen nur platziert werden können. Nur Menüs werden tatsächlich angezeigt, in der IDE, Gruppen und Befehle sind nicht.

-   Untermenüs ein Menü können nicht direkt zugewiesen werden, aber Sie müssen zu einer Gruppe, die wiederum ein Menü zugewiesen wird zugewiesen werden.

-   Befehle, Untermenüs und Gruppen können eine Überordnung Gruppe oder im Menü mithilfe des übergeordneten Felds ihrer definierenden Richtlinie zugewiesen werden.

-   Organisieren eine Befehlstabelle ausschließlich über die übergeordnete Felder in den Richtlinien ist eine wichtige Einschränkung. Die Direktiven, die Objekte definieren können nur ein übergeordnetes Element-Argument annehmen.

-   Wiederverwenden von Befehlen, Gruppen oder Untermenüs erfordert die Verwendung einer neuen Richtlinie so erstellen Sie eine neue Instanz des Objekts mit einem eigenen `GUID:ID` Paar.

-   Jede `GUID:ID` Paar muss eindeutig sein. Wiederverwenden eines Befehls, der z. B. in einem Menü, eine Symbolleiste oder in einem Kontextmenü platziert wurde, erfolgt durch die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle.

-   Befehle und Untermenüs können auch zu mehreren Gruppen zugewiesen werden, und Gruppen können zugewiesen werden, in mehreren Menüs mit der [Commands-Element](../../extensibility/commands-element.md).

## <a name="vsct-file-notes"></a>. Anmerkungen zu dieser VSCT-Datei
 Wenn Sie Änderungen in einer VSCT-Datei vornehmen, nachdem Sie sowohl kompilieren Sie ihn und fügen Sie ihn in eine systemeigene Satelliten-DLL, führen Sie **devenv.exe/Setup /nosetupvstemplates**. Dies erzwingt, dass die VSPackage-Ressourcen, die in der experimentellen Registrierung gelesen werden und die interne Datenbank, die beschreibt angegeben [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] neu erstellt werden.

 Während der Entwicklung ist es möglich, dass mehrere VSPackage-Projekte erstellt und in der experimentellen Registrierungsstruktur, die zu verwirrend übersichtliche in der IDE führen kann registriert werden. Um dieses Problem zu beheben, können Sie die experimentelle Struktur zurücksetzen, um die Standardeinstellungen, entfernen Sie alle registrierten VSPackages und alle Änderungen, die sie der IDE möglicherweise vorgenommen hat. Verwenden Sie die experimentelle Struktur zum Zurücksetzen der CreateExpInstance.exe-Tool, das in Visual Studio SDK enthalten ist. Sie finden ihn unter

 **% PROGRAMFILES (x 86) %\Visual Studio \<Version > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**

 Führen Sie das Tool mithilfe der Befehlszeile **CreateExpInstance/Reset**. Denken Sie daran, dass dieses Tool aus der experimentellen Struktur allen registrierten VSPackages, die normalerweise nicht mit installierten entfernt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Siehe auch
 [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md)