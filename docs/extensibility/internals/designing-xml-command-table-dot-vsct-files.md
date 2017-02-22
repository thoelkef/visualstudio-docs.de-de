---
title: "XML-Befehlstabelle entwerfen (. VSCT) Dateien | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Entwerfen von VSCT-Dateien"
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# XML-Befehlstabelle entwerfen (. VSCT) Dateien
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Eine XML\-Tabelle \(VSCT\) Datei beschreibt das Layout und die Darstellung der Elemente des Befehls für ein VSPackage. Befehl Elemente enthalten Schaltflächen, Kombinationsfelder, Menüs, Symbolleisten und Elementgruppen Befehl. Dieses Thema beschreibt die XML\-Befehlsdateien für die Tabelle, wie sie Befehl Elemente und Menüs auswirken und wie sie erstellt.  
  
## Befehle, Menüs, Gruppen und der VSCT\-Datei  
 VSCT\-Dateien sind Befehle, Menüs und Befehlsgruppen organisiert. Darstellen von XML\-Tags in der VSCT\-Datei jedes dieser Elemente, sowie andere zugehörige Elemente wie z. B. Schaltflächen, Befehl Platzierung und Bitmaps.  
  
 Beim Erstellen eines neuen VSPackages durch Ausführen der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Paketvorlage, die Vorlage generiert eine VSCT\-Datei mit der erforderlichen Elemente für einen Menübefehl, Toolfenster oder benutzerdefinierten Editor, abhängig von Ihrer Auswahl. Diese VSCT\-Datei kann dann die Bedürfnisse von einem bestimmten VSPackage geändert werden. Beispiele für das Ändern einer VSCT\-Datei finden Sie in die Beispielen in [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).  
  
 Um eine neue, leere VSCT\-Datei zu erstellen, finden Sie unter [Gewusst wie: Erstellen einer. VSCT\-Datei](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Nach dem Erstellen, fügen Sie XML\-Elemente, Attribute und Werte der Datei, die der Befehl das Elementlayout beschreiben. Eine ausführliche XML\-Schema finden Sie unter der [VSCT XML\-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md).  
  
## Unterschiede zwischen .ctc und VSCT\-Dateien  
 Während die Bedeutung der XML\-Tags in einer VSCT\-Datei identisch sind als die in der Gegenwart .ctc Dateiformat veraltet, unterscheidet sich ihre Implementierung.  
  
-   Die neue **\< Extern \>** Tag ist, in dem Sie andere h\-Dateien kompiliert werden, z. B. für verweisen die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Symbolleiste.  
  
-   Während VSCT Dateien zur Unterstützung der **\/ include** \-Anweisung, wie .ctc Dateien, es auch über das neue \<**Importieren \>** Element. Der Unterschied besteht darin, **\/ include** bringt in **alle** Informationen, aber \<**Importieren \>** bringt nur die Namen.  
  
-   Obwohl .ctc Dateien eine Headerdatei benötigen, in der Sie Ihre Präprozessordirektiven definieren, ist eine nicht für VSCT\-Dateien erforderlich. Stattdessen setzen die Richtlinien in der Symboltabelle befindet sich der **\< Symbol \>** Elemente, die am unteren Rand der .vsct\-Datei.  
  
-   VSCT\-Dateien\-Funktion ein **\< Anmerkung \>** \-Tag, das ermöglicht es Ihnen, alle Informationen einbetten, z. B. Hinweise oder auch Bilder möchten.  
  
-   Werte werden als Attribute für das Element gespeichert.  
  
-   Befehlsflags können einzeln gespeichert oder gestapelt werden.  IntelliSense funktioniert jedoch nicht auf gestapelte Befehlsflags. Weitere Informationen zu Befehlsflags, finden Sie unter der [Command\-Flag\-Element](../../extensibility/command-flag-element.md).  
  
-   Sie können mehrere Typen, z. B. Split Dropdownlisten, Tastenkürzel usw. angeben.  
  
-   GUIDs werden nicht überprüft.  
  
-   Jedes Element der Benutzeroberfläche ist eine Zeichenfolge, die den Text darstellt, mit der er angezeigt wird.  
  
-   Übergeordnete Element ist optional. Wenn nicht angegeben, wird der Wert "Unknown Gruppe" verwendet.  
  
-   Die Symbol\-Argument ist optional.  
  
-   Bereich "Bitmap" – identisch mit einer .ctc\-Datei, mit der Ausnahme, dass Sie jetzt einen Dateinamen über Href angeben können, die vom Compiler vsct.exe zum Zeitpunkt der Kompilierung herausgezogen werden.  
  
-   ResID\-\-die alten Bitmap\-Ressourcen\-ID kann verwendet werden, und weiterhin funktioniert wie .ctc\-Dateien.  
  
-   HRef – eine neue Methode, die Ihnen ermöglicht, einen Dateinamen für die Bitmapressource angeben. Es geht davon aus, dass alle verwendet werden, können Sie die verwendeten Abschnitt weglassen. Der Compiler sucht zuerst nach lokaler Ressourcen für die Datei, klicken Sie dann auf net Freigaben, und alle Ressourcen, die von der\/i\-Option definiert.  
  
-   KeyBinding – Sie müssen nicht mehr an einen Emulator. Wenn Sie angeben, wird der Compiler davon aus, dass der Editor und den Emulator identisch sind.  
  
-   Keychord\-\-wurde gelöscht. Das neue Format ist Key1 "," Mod1 "," Key2 "," Mod2.  Sie können ein Zeichen, Hexadezimal\- oder VK Konstante angeben.  
  
 Die neuen Compiler, vsct.exe, .ctc und VSCT\-Dateien kompiliert. Der alte ctc.exe Compiler jedoch weder erkennen noch VSCT\-Dateien zu kompilieren.  
  
 Den Compiler vsct.exe können Sie um eine vorhandene .cto\-Datei in eine VSCT\-Datei zu konvertieren. Weitere Informationen hierzu finden Sie unter [Gewusst wie: Erstellen einer VSCT\-Datei anhand einer vorhandenen CTO\-Datei](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
## Die Elemente der VSCT\-Datei  
 Die Befehlstabelle weist die folgenden Hierarchie und die folgenden Elemente:  
  
 [CommandTable\-Element](../../extensibility/commandtable-element.md) – Eine Auflistung aller Befehle, Menügruppen und Menüs des VSPackage zugeordnet.  
  
 [Extern\-Element](../../extensibility/extern-element.md) – Verweist auf eine beliebige externe h\-Dateien, mit der VSCT\-Datei zusammengeführt werden soll.  
  
 [Include\-Element](../../extensibility/include-element.md) – Verweist auf beliebige zusätzliche Headerdateien \(. h\), zusammen mit your.vsct\-Datei kompiliert werden soll. VSCT\-Datei zählen h\-Dateien mit Konstanten, die definieren Befehle, Menügruppen und Menüs, die den IDE\- oder einem anderen VSPackage bereitstellt.  
  
 [Commands\-Element](../../extensibility/commands-element.md) – Stellt alle für die einzelnen Befehle, die ausgeführt werden können. Jeder Befehl verfügt über die folgenden vier untergeordneten Elemente:  
  
 [Menüs\-Element](../../extensibility/menus-element.md) – Alle Menüs und Symbolleisten in das VSPackage darstellt. Menüs sind Container für Gruppen von Befehlen.  
  
 [Groups\-Element](../../extensibility/groups-element.md) — Steht für alle Gruppen in der VSPackage. Gruppen sind Sammlungen von einzelnen Befehle.  
  
 [Schaltflächen\-Element](../../extensibility/buttons-element.md) – Stellt alle Schaltflächen und Menüelemente in VSPackage. Schaltflächen sind visuelle Steuerelemente, die mit den Befehlen zugeordnet werden können.  
  
 [Bitmaps\-Element](../../extensibility/bitmaps-element.md) – Alle die Bitmaps für alle Schaltflächen in der VSPackage darstellt. Bitmaps sind Bilder, die neben oder auf die Befehlsschaltflächen, je nach Kontext anzeigen.  
  
 [CommandPlacements\-Element](../../extensibility/commandplacements-element.md) – Gibt zusätzliche Speicherorte, in denen die einzelnen Befehle in den Menüs der Ihr VSPackage platziert werden sollten.  
  
 [VisibilityConstraints\-Element](../../extensibility/visibilityconstraints-element.md) – Gibt an, ob ein Befehl zeigt alle Zeiten oder nur in bestimmten Kontexten, z. B. wenn ein bestimmtes Dialogfeld bzw. Fenster angezeigt wird. Menüs und Befehle, die keinen für dieses Element Wert zeigt nur, wenn der angegebene Kontext aktiv ist. Standardmäßig wird den Befehl immer angezeigt.  
  
 [KeyBindings\-Element](../../extensibility/keybindings-element.md) – Gibt alle Tastenkombinationen für Befehle. D. h. eine oder mehrere Tastenkombinationen, die gedrückt werden müssen, um den Befehl ausführen, wie z. B. **STRG \+ S**.  
  
 [UsedCommands\-Element](../../extensibility/usedcommands-element.md) – Informiert den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung, die zwar der angegebene Befehl durch anderen Code implementiert ist, wenn das aktuelle VSPackage aktiv ist, die Befehl Implementierung bereitstellt.  
  
 `Symbols Element` – Enthält die Symbolnamen und die GUID\-IDs für alle Befehle im Paket.  
  
## . Richtlinien zum Entwerfen der VSCT\-Datei  
 Richtlinien Sie die folgenden, um eine VSCT\-Datei erfolgreich zu entwerfen.  
  
-   Befehle können nur in Gruppen platziert werden, nur in Menüs Gruppen platziert werden und Menüs können nur in Gruppen platziert werden. Nur Menüs werden tatsächlich angezeigt, in der IDE, Gruppen und Befehle nicht.  
  
-   Untermenüs ein Menü nicht direkt zugewiesen werden, aber Sie müssen eine Gruppe, die wiederum ein Menü zugewiesen ist zugewiesen werden.  
  
-   Befehle, Untermenüs und Gruppen können eine Überordnung Gruppe oder ein Menü mithilfe des übergeordneten Felds ihrer definierenden Richtlinie zugewiesen werden.  
  
-   Organisieren eine Befehlstabelle ausschließlich über die übergeordnete Felder in den Richtlinien hat eine wichtige Einschränkung. Die Direktiven, die Objekte definieren, können nur ein übergeordnetes Element\-Argument annehmen.  
  
-   Wiederverwenden von Befehlen, Gruppen oder Untermenüs erfordert die Verwendung einer neuen Richtlinie so erstellen Sie eine neue Instanz des Objekts mit eigenen `GUID:ID` Paar.  
  
-   Jede `GUID:ID` Paar muss eindeutig sein. Wiederverwenden von einem Befehl, der z. B. auf ein Menü, eine Symbolleiste oder in einem Kontextmenü platziert wurde, wird anhand der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle.  
  
-   Befehle und Untermenüs können auch zu mehreren Gruppen zugewiesen werden, und Gruppen können mehrere Menüs mit zugewiesen werden die [Commands\-Element](../../extensibility/commands-element.md).  
  
## . Notes\-VSCT\-Datei  
 Wenn Sie keine an einer VSCT\-Datei Änderungen nach dem sowohl kompilieren Sie ihn und fügen Sie ihn in eine systemeigene Satelliten\-DLL, führen Sie **devenv.exe\/Setup \/nosetupvstemplates**. Auf diese Weise die VSPackage\-Ressourcen gemäß der experimentellen Registrierung abgelesen werden, und die interne Datenbank, die beschreibt, erzwingt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] neu erstellt werden.  
  
 Während der Entwicklung ist es möglich, dass mehrere VSPackage\-Projekten erstellt und registriert in der experimentellen Registrierungsstruktur, die zu verwirrenden Unordnung in der IDE führen kann. Um dieses Problem zu beheben, können Sie die experimentelle Struktur zurücksetzen auf die Standardeinstellungen zum Entfernen aller registrierten VSPackages und alle Änderungen, die sie in die IDE erstellt haben. Verwenden Sie zum Zurücksetzen der experimentellen Struktur das CreateExpInstance.exe\-Tool, das in Visual Studio SDK enthalten ist. Sie finden sie unter  
  
 **% PROGRAMFILES \(x 86\) %\\Visual Studio \< Version \> SDK\\VisualStudioIntegration\\Tools\\Bin\\CreateExpInstance.exe**  
  
 Führen Sie das Tool mithilfe der Befehlszeile **CreateExpInstance\/Reset**. Beachten Sie, dass dieses Tool aus der experimentellen Struktur entfernt werden alle registrierten VSPackages normalerweise nicht mit installiert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Siehe auch  
 [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md)