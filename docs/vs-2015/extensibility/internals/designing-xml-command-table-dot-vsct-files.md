---
title: Entwerfen von XML-Befehlstabelle (. VSCT)-Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6c7a4e07c45c5d651af057e1eb33c23d37601cb3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762808"
---
# <a name="designing-xml-command-table-vsct-files"></a>Entwerfen von XML-Befehlstabelle (. VSCT)-Dateien
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Eine XML-Befehlstabellen (VSCT) Befehlsdatei beschreibt das Layout und die Darstellung der Befehl-Elemente für ein VSPackage. Befehls-Elemente enthalten, Schaltflächen, Kombinationsfelder, Menüs, Symbolleisten und Gruppen von Elementen für Befehl. Dieses Thema beschreibt die XML-Befehlsdateien für die Tabelle, wie sie Befehl-Elemente und Menüs auswirken und zu deren Erstellung.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>Befehle, Menüs, Gruppen und der VSCT-Datei  
 VSCT-Dateien sind auf Befehlsgruppen, Menüs und Befehle organisiert. Darstellen von XML-Tags in der VSCT-Datei jedes dieser Elemente, zusammen mit anderen zugehörigen Elementen wie z. B. Schaltflächen, Befehl Platzierung und Bitmaps.  
  
 Wenn Sie ein neues VSPackage erstellen, mit der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Paket-Vorlage, die Vorlage generiert eine VSCT-Datei mit der erforderlichen Elemente für einen Menübefehl, Toolfenster oder benutzerdefinierten Editor, abhängig von Ihrer Auswahl. Diese VSCT-Datei kann dann für die ein bestimmtes VSPackage Anforderungen geändert werden. Beispiele für die Vorgehensweise beim Ändern einer VSCT-Datei finden Sie in die Beispielen in [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).  
  
 Um eine neue, leere VSCT-Datei zu erstellen, finden Sie unter [Vorgehensweise: Erstellen Sie ein. VSCT-Datei](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Nach der Erstellung, fügen Sie XML-Elemente, Attribute und Werte in die Datei, um das Layout der Befehl-Element zu beschreiben. Eine detaillierte XML-Schema finden Sie unter den [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Unterschiede zwischen CTC und VSCT-Dateien  
 Die Bedeutung der XML-Tags in einer VSCT-Datei identisch sind als diejenigen, die jetzt CTC-Dateiformat veraltet, ist ihre Implementierung ein wenig anders.  
  
- Die neue  **\<"extern" >** Tag ist, in denen Sie kompiliert werden, etwa solche für andere .h-Dateien verweisen die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Symbolleiste.  
  
- Während der VSCT-Dateien unterstützen die **/ include** -Anweisung, wie CTC-Dateien, es auch über das neue \< **Importieren >** Element. Der Unterschied besteht darin, **/ include** bringt in **alle** die Informationen, aber \< **Importieren >** ermöglicht nur die Namen.  
  
- Während der CTC-Dateien eine Headerdatei erfordern in der Sie Ihre Präprozessordirektiven definieren, muss eine nicht für die VSCT-Dateien. Ordnen Sie stattdessen die Anweisungen in der Symboltabelle, befindet sich in der  **\<Symbol >** Elemente, die am unteren Rand der VSCT-Datei.  
  
- VSCT-Dateien-Funktion eine  **\<Annotation >** -Tag, sodass Sie alle Informationen betten Sie zufrieden sind, z. B. Notizen oder auch Bilder.  
  
- Werte werden als Attribute für das Element gespeichert.  
  
- Befehlsflags können einzeln gespeichert oder gestapelt werden.  IntelliSense, funktioniert jedoch nicht auf gestapelte Befehlsflags. Weitere Informationen zu Befehlsflags, finden Sie unter den [Commandflag-Element](../../extensibility/command-flag-element.md).  
  
- Sie können mehrere Typen, z. B. Split Dropdownlisten, Combos usw. angeben.  
  
- GUIDs werden nicht überprüft.  
  
- Jedes Element der Benutzeroberfläche hat eine Zeichenfolge, die den Text darstellt, der dabei angezeigt wird.  
  
- Übergeordnete Element ist optional. Wenn nicht angegeben, wird der Wert, der "Gruppe unbekannt" verwendet.  
  
- Das Symbol "-Argument ist optional.  
  
- Bereich "Bitmap"--identisch mit einer CTC-Datei, mit dem Unterschied, dass Sie jetzt einen Dateinamen über Href angeben können, die vom Compiler vsct.exe zum Zeitpunkt der Kompilierung herausgezogen werden.  
  
- "RESID" – die alte Ressourcen-ID der Bitmap verwendet werden kann und weiterhin funktioniert genauso wie in der CTC-Dateien.  
  
- HRef: eine neue Methode, die Sie einen Namen für die Bitmapressource angeben kann. Es wird davon ausgegangen, dass alle verwendet werden, damit Sie die verwendete Bereich weglassen können. Der Compiler sucht zuerst nach lokaler Ressourcen für die Datei, klicken Sie dann auf net Freigaben, und alle Ressourcen, die vom Schalter/i definiert.  
  
- Tastenzuordnung: Sie müssen nicht mehr an einen Emulator. Wenn Sie angeben, wird der Compiler davon aus, dass der Editor und den Emulator identisch sind.  
  
- Keychord--wurde gelöscht. Das neue Format ist "Key1" "," Mod1 "," Key2 "," Mod2.  Sie können entweder ein Zeichen, Hexadezimalwert oder VK Konstante angeben.  
  
  Die neuen Compiler, vsct.exe, kompiliert sowohl CTC-VSCT-Dateien. Der alten ctc.exe-Compiler, jedoch werden weder erkannt noch VSCT-Dateien zu kompilieren.  
  
  Sie können den Compiler vsct.exe verwenden, um einer vorhandenen CTO-Datei in eine VSCT-Datei zu konvertieren. Weitere Informationen hierzu finden Sie unter [Vorgehensweise: Erstellen Sie ein. VSCT-Datei aus einem vorhandenen. CTO-Datei](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
## <a name="the-vsct-file-elements"></a>Die Elemente der VSCT-Datei  
 Die Befehlstabelle weist die folgende Hierarchie und die folgenden Elemente:  
  
 [CommandTable-Element](../../extensibility/commandtable-element.md) – repräsentiert alle Befehle, Menügruppen und Menüs, die das VSPackage zugeordnet.  
  
 [Extern-Element](../../extensibility/extern-element.md) – verweist auf externe .h-Dateien, die Sie mit der VSCT-Datei zusammenführen möchten.  
  
 [Include-Element](../../extensibility/include-element.md) – verweist auf zusätzlichen Header (. h)-Dateien, die Sie zusammen mit your.vsct-Datei kompilieren möchten. Eine VSCT-Datei zählen .h-Dateien, enthält die Konstanten an, die definieren Befehle, Menügruppen und Menüs, die die IDE oder einem anderen VSPackage bereitstellt.  
  
 [Befehle Element](../../extensibility/commands-element.md) – repräsentiert alle der einzelnen Befehle, die ausgeführt werden können. Jeder Befehl verfügt über die folgenden vier untergeordneten Elemente:  
  
 [Menus-Element](../../extensibility/menus-element.md) – repräsentiert alle Menüs und Symbolleisten in das VSPackage. Menüs sind Container für Gruppen von Befehlen.  
  
 [Element für Gruppen](../../extensibility/groups-element.md) – alle Gruppen im VSPackage darstellt. Gruppen sind Sammlungen der einzelnen Befehle.  
  
 [Element Schaltflächen](../../extensibility/buttons-element.md) – alle Schaltflächen und Menüelemente im VSPackage darstellt. Schaltflächen sind visuellen Steuerelementen, die mit den Befehlen zugeordnet werden können.  
  
 [Bitmaps-Element](../../extensibility/bitmaps-element.md) – repräsentiert alle die Bitmaps für alle Schaltflächen im VSPackage. Bitmaps sind Bilder, die neben oder auf die Befehlsschaltflächen, je nach Kontext anzeigen.  
  
 [CommandPlacements-Element](../../extensibility/commandplacements-element.md) – gibt an, dass zusätzliche Standorte, in denen die einzelnen Befehle in den Menüs Ihres VSPackage positioniert werden soll.  
  
 [VisibilityConstraints-Element](../../extensibility/visibilityconstraints-element.md) – gibt an, und zwar unabhängig davon, ob ein Befehl zeigt alle, oder nur in bestimmten Kontexten wie z. B. wenn ein bestimmtes Dialogfeld oder Fenster angezeigt wird. Menüs und Befehle, die einen Wert für dieses Element zeigt nur, wenn der angegebene Kontext aktiv ist. Das Standardverhalten ist, um den Befehl jederzeit anzuzeigen.  
  
 [KeyBindings-Element](../../extensibility/keybindings-element.md) – gibt an, alle tastenzuordnungen für die Befehle. D. h. ein oder mehrere Tastenkombinationen, die gedrückt werden müssen, führen Sie den Befehl ein, z. B. **STRG + S**.  
  
 [UsedCommands-Element](../../extensibility/usedcommands-element.md) – Informs der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Umgebung aus, auch wenn der angegebene Befehl durch anderen Code implementiert wird, wenn das aktuelle VSPackage aktiv ist, die befehlsimplementierung enthält.  
  
 `Symbols Element` – Enthält die Symbolnamen und die GUID-IDs für alle Ihre Befehle im Paket.  
  
## <a name="vsct-file-design-guidelines"></a>. Richtlinien zum Entwerfen der VSCT-Datei  
 Beachten Sie Folgendes, um eine VSCT-Datei erfolgreich zu entwerfen.  
  
-   Befehle können nur in Gruppen befinden, Gruppen platziert werden können, nur in Menüs und Menüs in Gruppen nur platziert werden können. Nur die Menüs werden tatsächlich angezeigt, in der IDE, Gruppen und Befehle nicht.  
  
-   Untermenüs ein Menü können nicht direkt zugewiesen werden, jedoch müssen zugewiesen werden, um eine Gruppe, die wiederum zu einem Menü zugewiesen wird.  
  
-   Befehle, Untermenüs und Gruppen können eine übergeordnete Gruppe oder ein Menü, die mithilfe des übergeordneten Felds ihrer Richtlinie definieren zugewiesen werden.  
  
-   Organisieren eine Befehlstabelle ausschließlich über die übergeordnete Felder in den Richtlinien ist eine wichtige Einschränkung. Die Anweisungen, die Objekte zu definieren, können nur ein übergeordnetes Argument dauern.  
  
-   Wiederverwenden von Befehlen, Gruppen oder Untermenüs erfordert die Verwendung von eine neue Richtlinie erstellen Sie eine neue Instanz des Objekts durch einen eigenen `GUID:ID` Paar.  
  
-   Jede `GUID:ID` -Paar muss eindeutig sein. Wiederverwenden eines Befehls, der z. B. in einem Menü, eine Symbolleiste, oder in einem Kontextmenü platziert wurde, erfolgt durch die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle.  
  
-   Befehle und Untermenüs können auch zu mehreren Gruppen zugewiesen werden, und mehrere Menüs, die mithilfe von Gruppen zugewiesen werden die [Commands-Element](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. Anmerkungen zu dieser VSCT-Datei  
 Wenn Sie Änderungen in einer VSCT-Datei vornehmen, nachdem Sie sowohl kompilieren Sie ihn und fügen Sie ihn in einer systemeigenen Satelliten-DLL, führen Sie **devenv.exe/Setup /nosetupvstemplates**. Dies erzwingt, dass die VSPackage-Ressourcen, die in der experimentellen Registrierung abgelesen werden, und die interne Datenbank, die beschreibt, angegeben [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] neu erstellt werden.  
  
 Während der Entwicklung ist es möglich, dass mehrere VSPackage-Projekte erstellt und in der experimentellen Registrierungsstruktur, die zu verwirrend Überfrachtung in der IDE führen kann registriert werden. Um dieses Problem zu beheben, können Sie die experimentelle Struktur zurücksetzen, um die Standardeinstellungen, entfernen Sie alle registrierten VSPackages und alle Änderungen, die sie der IDE vorgenommen haben, können. Verwenden Sie zum Zurücksetzen der experimentellen Struktur das CreateExpInstance.exe-Tool, das in Visual Studio SDK enthalten ist. Sie finden sie unter  
  
 **% PROGRAMFILES (x 86) %\Visual Studio \<Version > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Führen Sie das Tool über die Befehlszeile **CreateExpInstance/Reset**. Denken Sie daran, dass dieses Tool aus der experimentellen Struktur, alle registrierte VSPackages, die normalerweise nicht entfernt mit installierten [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md)

