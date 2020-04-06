---
title: Entwerfen der XML-Befehlstabelle (. Vsct) Dateien | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcd29aee98139bb151c87590b256df6b8370abff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708744"
---
# <a name="design-xml-command-table-vsct-files"></a>Entwerfen von XML-Befehlstabellendateien (.vsct)
Eine XML-Befehlstabelle (*.vsct*) -Datei beschreibt das Layout und die Darstellung von Befehlselementen für ein VSPackage. Zu den Befehlselementen gehören Schaltflächen, Kombinationsfelder, Menüs, Symbolleisten und Gruppen von Befehlselementen. In diesem Artikel werden XML-Befehlstabellendateien, deren Auswirkungen auf Befehlselemente und Menüs und deren Erstellung beschrieben.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Befehle, Menüs, Gruppen und die .vsct-Datei
 Die *.vsct-Dateien* sind um Befehle, Menüs und Befehlsgruppen organisiert. XML-Tags in der *.vsct-Datei* stellen jedes dieser Elemente zusammen mit anderen zugeordneten Elementen wie Befehlsschaltflächen, Befehlsplatzierung und Bitmaps dar.

 Wenn Sie ein neues VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] erstellen, indem Sie die Paketvorlage ausführen, generiert die Vorlage je nach Auswahl eine *.vsct-Datei* mit den erforderlichen Elementen für einen Menübefehl, ein Toolfenster oder einen benutzerdefinierten Editor. Diese *.vsct-Datei* kann dann geändert werden, um die Anforderungen eines bestimmten VSPackage zu erfüllen. Beispiele zum Ändern einer *.vsct-Datei* finden Sie unter Erweitern von [Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).

 Informationen zum Erstellen einer neuen, leeren *.vsct-Datei* finden Sie unter [Gewusst wie: Erstellen einer *.vsct-Datei* ](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Nach der Erstellung fügen Sie der Datei XML-Elemente, Attribute und Werte hinzu, um das Befehlselementlayout zu beschreiben. Ein detailliertes XML-Schema finden Sie im [VSCT-XML-Schemaverweis](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>Unterschiede zwischen .ctc- und .vsct-Dateien
 Während die Bedeutung hinter den XML-Tags in einer *.vsct-Datei* mit den Tags im jetzt veralteten *.ctc-Dateiformat* identisch ist, ist ihre Implementierung etwas anders:

- Das ** \<** neue>-Tag verweist auf andere zu kompilierende *H-Dateien,* z. B. Dateien für die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Symbolleiste.

- Während *.vsct-Dateien* die **/include-Anweisung** unterstützen, wie *es .ctc-Dateien* tun, verfügt sie auch über einen neuen ** \<Import->-Element.** Der Unterschied ist, **/include** bringt *alle* Informationen ein, während ** \<Import->** nur die Namen einbringt.

- Während *.ctc-Dateien* eine Headerdatei erfordern, in der Sie Ihre Präprozessordirektiven definieren, ist eine für *.vsct-Dateien* nicht erforderlich. Platzieren Sie stattdessen Ihre Direktiven in ** \<** der Symboltabelle, die sich im Symbol->-Elementen am unteren Rand der *.vsct-Datei* befindet.

- *.vsct* Dateien ** \<** verfügen über eine Anmerkung>Tag, mit dem Sie alle Informationen einbetten können, die Sie mögen, wie Notizen oder sogar Bilder.

- Werte werden als Attribute für das Element gespeichert.

- Befehlsflags können einzeln oder gestapelt gespeichert werden.  IntelliSense funktioniert jedoch nicht auf gestapelten Befehlsflags. Weitere Informationen zu Befehlsflags finden Sie im [CommandFlag-Element](../../extensibility/command-flag-element.md).

- Sie können mehrere Typen angeben, z. B. geteilte Dropdowns, Kombinationen usw.

- GUIDs werden nicht überprüft.

- Jedes UI-Element verfügt über eine Zeichenfolge, die den damit angezeigten Text darstellt.

- Das übergeordnete Element ist optional. Wenn nicht angegeben, wird der Wert *Gruppe Unbekannt* verwendet.

- Das *Argument Icon* ist optional.

- Bitmap-Abschnitt: Dieser Abschnitt ist derselbe wie in einer *.ctc-Datei,* mit der Ausnahme, dass Sie jetzt einen Dateinamen über Href angeben können, der vom *vsct.exe-Compiler* zur Kompilierungszeit eingezogen wird.

- ResID: Die alte Bitmap-Ressourcen-ID kann verwendet werden und funktioniert immer noch genauso wie in *CTC-Dateien.*

- HRef: Eine neue Methode, mit der Sie einen Dateinamen für die Bitmapressource angeben können. Es wird davon ausgegangen, dass alle verwendet werden, sodass Sie den Abschnitt Verwendet weglassen können. Der Compiler sucht zunächst nach lokalen Ressourcen für die Datei, dann nach allen Netzfreigaben und allen Ressourcen, die durch den Schalter **/I** definiert werden.

- Schlüsselbindung: Sie müssen keinen Emulator mehr angeben. Wenn Sie eine angeben, geht der Compiler davon aus, dass der Editor und der Emulator identisch sind.

- Keychord: Keychord wurde fallen gelassen. Das neue Format ist *Key1,Mod1,Key2,Mod2*.  Sie können entweder ein Zeichen, eine hexadezimale oder eine VK-Konstante angeben.

Der neue *Compiler, vsct.exe*, kompiliert sowohl *.ctc-* als auch *.vsct-Dateien.* Der alte *ctc.exe-Compiler* erkennt oder kompiliert *jedoch keine .vsct-Dateien.*

Sie können den *Compiler vsct.exe* verwenden, um eine vorhandene *.cto-Datei* in eine *.vsct-Datei* zu konvertieren. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen einer .vsct-Datei aus einer vorhandenen Cto-Datei](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

## <a name="the-vsct-file-elements"></a>Die .vsct-Dateielemente
 Die Befehlstabelle enthält die folgenden Hierarchien und Elemente:

- [CommandTable-Element](../../extensibility/commandtable-element.md): Stellt alle Befehle, Menügruppen und Menüs dar, die dem VSPackage zugeordnet sind.

- [Externes Element](../../extensibility/extern-element.md): Verweist auf alle externen .h-Dateien, die Sie mit der *.vsct-Datei* zusammenführen möchten.

- [Include-Element](../../extensibility/include-element.md): Verweist auf alle zusätzlichen Headerdateien (.h), die Sie zusammen mit Ihrer *.vsct-Datei* kompilieren möchten. Eine *.vsct-Datei* kann *.h-Dateien enthalten,* die Konstanten enthalten, die Befehle, Menügruppen und Menüs definieren, die die IDE oder ein anderes VSPackage bereitstellt.

- [Befehlselement](../../extensibility/commands-element.md): Stellt alle einzelnen Befehle dar, die ausgeführt werden können. Jeder Befehl enthält die folgenden vier untergeordneten Elemente:

- [Menüs-Element](../../extensibility/menus-element.md): Stellt alle Menüs und Symbolleisten im VSPackage dar. Menüs sind Container für Befehlsgruppen.

- [Groups-Element](../../extensibility/groups-element.md): Stellt alle Gruppen im VSPackage dar. Gruppen sind Auflistungen einzelner Befehle.

- [Buttons-Element](../../extensibility/buttons-element.md): Stellt alle Befehlsschaltflächen und Menüelemente im VSPackage dar. Schaltflächen sind visuelle Steuerelemente, die Befehlen zugeordnet werden können.

- [Bitmaps-Element](../../extensibility/bitmaps-element.md): Stellt alle Bitmaps für alle Schaltflächen im VSPackage dar. Bitmaps sind Bilder, die je nach Kontext neben oder auf den Befehlsschaltflächen angezeigt werden.

- [CommandPlacements-Element](../../extensibility/commandplacements-element.md): Gibt zusätzliche Speicherorte an, an denen die einzelnen Befehle in den Menüs Ihres VSPackage platziert werden sollen.

- [VisibilityConstraints-Element](../../extensibility/visibilityconstraints-element.md): Gibt an, ob ein Befehl jederzeit oder nur in bestimmten Kontexten angezeigt wird, z. B. wenn ein bestimmtes Dialogfeld oder Fenster angezeigt wird. Menüs und Befehle, die einen Wert für dieses Element haben, werden nur angezeigt, wenn der angegebene Kontext aktiv ist. Das Standardverhalten besteht darin, den Befehl jederzeit anzuzeigen.

- [KeyBindings-Element](../../extensibility/keybindings-element.md): Gibt alle Schlüsselbindungen für die Befehle an. Das heißt, eine oder mehrere Tastenkombinationen, die gedrückt werden müssen, um den Befehl auszuführen, z. **B. Strg**+**S**.

- [UsedCommands-Element](../../extensibility/usedcommands-element.md): [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Informiert die Umgebung, dass der angegebene Befehl zwar von anderem Code implementiert wird, wenn das aktuelle VSPackage aktiv ist, die Befehlsimplementierung jedoch bereitstellt.

- [Symbols-Element](../../extensibility/symbols-element.md): Enthält die Symbolnamen und GUID-IDs für alle Befehle im Paket.

## <a name="vsct-file-design-guidelines"></a>.vsct Dateidesign-Richtlinien
 Um eine *.vsct-Datei* erfolgreich zu entwerfen, befolgen Sie diese Richtlinien.

- Befehle können nur in Gruppen platziert werden, Gruppen können nur in Menüs und Menüs nur in Gruppen platziert werden. In der IDE werden nur Menüs angezeigt, Gruppen und Befehle nicht.

- Untermenüs können nicht direkt einem Menü zugewiesen werden, sondern müssen einer Gruppe zugewiesen werden, die wiederum einem Menü zugewiesen ist.

- Befehle, Untermenüs und Gruppen können einer übergeordneten Gruppe oder einem Menü mithilfe des übergeordneten Felds ihrer definierenden Direktive zugewiesen werden.

- Das Organisieren einer Befehlstabelle ausschließlich über die übergeordneten Felder in den Direktiven hat eine erhebliche Einschränkung. Die Direktiven, die Objekte definieren, können nur ein übergeordnetes Argument annehmen.

- Das Wiederverwenden von Befehlen, Gruppen oder Untermenüs erfordert die Verwendung einer `GUID:ID` neuen Direktive, um eine neue Instanz des Objekts mit einem eigenen Paar zu erstellen.

- Jedes `GUID:ID` Paar muss eindeutig sein. Die Wiederverwendung eines Befehls, der z. B. in einem Menü, einer Symbolleiste <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oder in einem Kontextmenü abgelegt wurde, wird von der Schnittstelle behandelt.

- Befehle und Untermenüs können auch mehreren Gruppen zugewiesen werden, und Gruppen können mithilfe des [Befehlselements](../../extensibility/commands-element.md)mehreren Menüs zugewiesen werden.

## <a name="vsct-file-notes"></a>.vsct Dateinotizen
 Wenn Sie Änderungen an einer *.vsct-Datei* vornehmen, nachdem Sie sie kompiliert und in einer nativen Satelliten-DLL platziert haben, sollten Sie **devenv.exe /setup /nosetupvstemplates**ausführen. Dadurch werden die in der experimentellen Registrierung angegebenen VSPackage-Ressourcen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] erneut gelesen und die interne Datenbank, die beschreibt, dass sie neu erstellt werden soll.

 Während der Entwicklung ist es möglich, dass mehrere VSPackage-Projekte erstellt und in der experimentellen Registrierungsstruktur registriert werden, was zu verwirrendem Durcheinander in der IDE führen kann. Um dies zu beheben, können Sie die experimentelle Struktur auf die Standardeinstellungen zurücksetzen, um alle registrierten VSPackages und alle Änderungen zu entfernen, die sie möglicherweise an der IDE vorgenommen haben. Um die experimentelle Struktur zurückzusetzen, verwenden Sie das Tool CreateExpInstance.exe, das im Zusammenhang mit dem Visual Studio SDK enthalten ist. Sie finden es unter:

 *%PROGRAMFILES(x86)%-Visual\\\<Studio-Version> SDK-VisualStudioIntegration-Tools,Bin-CreateExpInstance.exe*

 Führen Sie das Tool mit dem Befehl **CreateExpInstance /Reset**aus. Denken Sie daran, dass dieses Tool alle registrierten VSPackages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]aus der experimentellen Struktur entfernt, die normalerweise nicht mit installiert sind.

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md)
