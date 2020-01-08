---
title: Einfügen von XML-Dokumentationskommentaren
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ad29957cc31247c16ca38038ad4880ea75a85182
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595578"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Vorgehensweise: Einfügen von XML-Kommentaren für die Generierung der Dokumentation

Visual Studio unterstützt Sie dabei, Codeelemente wie z.B. Klassen und Methoden zu dokumentieren, indem es automatisch die Standardstruktur für XML-Dokumentationskommentare generiert. Sie können eine XML-Datei zur Kompilierzeit erstellen, die die Dokumentationskommentare enthält.

> [!TIP]
> Informationen zum Konfigurieren des Namens und des Speicherorts der erzeugten XML-Datei finden Sie unter [Dokumentieren von Code mit XML-Kommentaren (C# Guide)](/dotnet/csharp/codedoc).

Die vom Compiler generierte XML-Datei kann zusammen mit Ihrer .NET-Assembly verteilt werden, damit Visual Studio und andere IDEs mit IntelliSense QuickInfos über Typen und Member anzeigen können. Darüber hinaus kann die XML-Datei mithilfe von Tools wie [DocFX](https://dotnet.github.io/docfx/) und [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) ausgeführt werden, um API-Verweiswebsites zu generieren.

> [!NOTE]
> Der Befehl **Kommentar einfügen**, der automatisch XML-Dokumentationskommentare einfügt, ist in [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) und [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation) verfügbar. Dennoch können Sie [XML-Dokumentationskommentare in C++-Dateien](/cpp/build/reference/xml-documentation-visual-cpp) manuell einfügen, und weiterhin XML-Dokumentationskommentare zur Kompilierzeit generieren.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Einfügen von XML-Kommentaren für ein Codeelement

1. Platzieren Sie den Textcursor oberhalb des zu dokumentierenden Elements, z.B. einer Methode.

1. Führen Sie einen der folgenden Schritte aus:

   - Geben Sie `///` in C# oder `'''` in Visual Basic ein

   - Wählen Sie im Menü **Bearbeiten** **IntelliSense** > **Kommentar einfügen** aus.

   - Führen Sie einen Rechtsklick aus, bzw. nutzen Sie das Kontextmenü, und klicken dann auf **Ausschnitt** > **Kommentar einfügen**.

   Die XML-Vorlage wird sofort über dem Codeelement generiert. Wenn Sie zum Beispiel eine Methode kommentieren, wird ein **\<Summary\>** -Element, ein **\<param\>** -Element für jeden Parameter und ein **\<returns\>** -Element generiert, um den Rückgabewert zu dokumentieren.

   ![XML-Kommentarvorlage – C#](media/doc-preview-cs.png)

   ![XML-Kommentarvorlage – Visual Basic](media/doc-preview-vb.png)

1. Geben Sie Beschreibungen für jedes XML-Element an, um das Codeelement vollständig zu dokumentieren.

   ![Vervollständigter Kommentar](media/doc-result-cs.png)

> [!NOTE]
> Es gibt eine [Option](../../ide/reference/options-text-editor-csharp-advanced.md) zum Ein- und Ausblenden von XML-Dokumentationskommentaren nach der Eingabe von `///` in C# oder `'''` in Visual Basic. Wählen Sie in der Menüleiste **Extras** > **Optionen** aus, um das Dialogfeld **Optionen** zu öffnen. Navigieren Sie dann zu **Text-Editor** > **C#** oder **Basic** > **Advanced** (Basic > Erweitert). Suchen Sie im Abschnitt **Editor-Hilfe** nach der Option **XML-Dokumentationskommentare generieren**.

## <a name="see-also"></a>Siehe auch

- [XML-Dokumentationskommentare (C#-Programmierhandbuch)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documenting your code with XML comments (C# Guide) (Dokumentieren von Code mit XML-Kommentaren (C#-Handbuch))](/dotnet/csharp/codedoc)
- [Vorgehensweise: How to: Create XML documentation (Visual Basic) (Vorgehensweise: Erstellen von XML-Dokumentation in Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [C++-Kommentare](/cpp/cpp/comments-cpp)
- [XML-Dokumentation (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Codegenerierung](../code-generation-in-visual-studio.md)
