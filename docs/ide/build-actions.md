---
title: Buildprozesse für Dateien
ms.date: 11/19/2018
ms.technology: vs-ide-compile
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7820cbbe0477000c2a822e94f5204906d65025fa
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55950707"
---
# <a name="build-actions"></a>Buildvorgänge

Sämtliche Dateien in einem Projekt von Visual Studio verfügen über einen Buildprozess. Durch den Buildprozess wird kontrolliert, was mit der Datei passiert, wenn das Projekt erstellt ist.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Buildprozesse in Visual Studio für Mac](/visualstudio/mac/build-actions).

## <a name="set-a-build-action"></a>Festlegen eines Buildprozesses

Öffnen Sie die Eigenschaften der Datei im Fenster **Eigenschaften** durch Auswahl der Datei im **Projektmappen-Explorer**, und drücken Sie **Alt**+**Eingabe**, um den Buildprozess für eine Datei festzulegen. Oder klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Datei, und wählen Sie **Eigenschaften**. Verwenden Sie im Fenster **Eigenschaften** unter **Erweitert** die Dropdownliste neben **Buildprozess**, um einen Buildprozess für die Datei festzulegen.

![Buildprozesse für eine Datei in Visual Studio](media/build-actions.png)

## <a name="build-action-values"></a>Buildprozesswerte

Einige der Buildprozesse für C# und Visual Basic-Projektdateien sind die folgenden:

* **None** (Keiner): Die Datei ist in keiner Weise Teil des Builds. Dieser Wert kann für Dokumentationsdateien wie Infodateien verwendet werden.
* **Compile** (Kompilieren): Die Datei wird an den C#-Compiler als Quelldatei übergeben.
* **Content** (Inhalt): Eine Datei, die als **Inhalt** markiert ist, kann als Stream abgerufen werden, indem Sie <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType> aufrufen. Bei ASP.NET-Projekten werden diese Dateien bei der Bereitstellung als Teil der Website integriert.
* **Embedded Ressource** (Eingebettete Ressource): Die Datei wird an den Compiler als Ressource übergeben, die in die Assembly eingebettet wird. Rufen Sie <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> zum Lesen der Datei aus der Assembly auf.
* **Additional Files** (Zusätzliche Dateien): Eine Textdatei, die keine Quelldatei ist, die an den C#- oder Visual Basic-Compiler als Eingabe übergeben wird. Dieser Buildprozess wird hauptsächlich zum Bereitstellen von Eingaben für [Analysetools](../code-quality/roslyn-analyzers-overview.md) verwendet, auf die ein Projekt verweist, um die Codequalität zu überprüfen. Weitere Informationen finden Sie in der GitHub-Übersicht zum [Verwenden zusätzlicher Dateien](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md).

## <a name="see-also"></a>Siehe auch

- [C#-Compileroptionen](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Visual Basic-Compileroptionen](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Buildprozesse (Visual Studio für Mac)](/visualstudio/mac/build-actions)