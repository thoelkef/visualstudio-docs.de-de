---
title: VSCT Compiler-Befehlszeilenflags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4ee29710049453c3163c366eccf96e257b6028d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703959"
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT-Compiler-Befehlszeilenflags
Der Visual Studio-Befehlstabellencompiler (VSCT) stellt Befehlszeilenwechsel bereit, um eine erfolgreiche Kompilierung von .vsct-Dateien sicherzustellen.

## <a name="command-line-parameters"></a>Befehlszeilenparameter
 Um die grundlegende VSCT-Hilfe aus einem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Befehlsfenster** anzuzeigen, navigieren Sie zum Installationspfad des Visual Studio *SDK-Ordners*"VisualStudioIntegration" und geben Sie den folgenden Typ ein:

```
vsct /?
```

 Gibt Folgendes zurück:

```
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000

Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]

  -D    Specify any additional preprocessor defines
  -I    Indicate what additional include paths to send to the preprocessor
  -L    Specify the language to use when selecting strings
  -E    Emit C# objects in the specified namespace for command items,
        followed by [L|F|H|N]:<value>
        F = Name of the file to emit (used if -EL is provided)
        L = Name of a language providing a CodeDOM provider
        N = namespace (required if -EL is provided)
        H = C++ header
  -c    Clean build skipping dependency checks
  -v    Verbose output
```

> [!NOTE]
> Die Zeichen - (Dash) und / (Forward Slash) sind beide akzeptierte Notation für die Angabe von Befehlszeilenparametern.

 Akzeptable Flaggen und was sie bedeuten, sind wie folgt.

|Schalter|BESCHREIBUNG|
|------------|-----------------|
|-d|Geben Sie alle zusätzlichen definierten Symbole an.|
|-I|Geben Sie die zusätzlichen Includepfade an, die beim Auflösen von Dateiverweisen verwendet werden sollen.|
|-l|Geben <xref:System.Globalization.CultureInfo> Sie den Kulturnamen an, z. B. "en-US".|
|-E|Emit-C-Objekte im angegebenen Namespace für Befehlselemente, gefolgt von [C&#124;H&#124;N]:*Dateiname,* wobei C = C, H = C++-Header, N = Namespace. Der Namespace ist für C- erforderlich.|
|-v|Ausführliche Ausgabe.|

 Der Schalter -L weist den Compiler an, eine Gruppe von Zeichenfolgen auszuwählen, <xref:System.Globalization.CultureInfo> um die binäre .cto-Datei zu erzeugen, die dem angegebenen Kulturnamen entspricht. Der angegebene Kulturname sollte mit dem Language-Attribut eines oder mehrerer [Strings-Elemente](../../extensibility/strings-element.md) in der .vsct-Datei übereinstimmen. Wenn ein Strings-Element kein Language-Attribut hat, wird es vom enthaltenden [CommandTable-Element](../../extensibility/commandtable-element.md)geerbt.

 Eine .vsct-Datei kann über mehrere Strings-Elemente verfügen, und jedes kann ein anderes Language-Attribut haben. Die Globalisierung wird erreicht, indem der VSCT-Compiler mehrmals ausgeführt und der Schalter -L für jeden Kulturnamen geändert wird.

 Wenn der vom Schalter -L angegebene Kulturname nicht mit dem Language-Attribut eines Strings-Elements übereinstimmt, versucht der Compiler, der Sprache und nicht der Region zu entsprechen. Wenn z. B. "en-US" nicht gefunden werden kann, versucht der Compiler stattdessen "en". Andernfalls wird die aktuelle Kultur des Betriebssystems ausprobiert. Andernfalls wird das erste gefundene Strings-Element kompiliert.

 Der Schalter -E kann verwendet werden, um eine Headerdatei im C-Stil auszusenden, die die Symbole enthält, die von der Befehlstabelle verwendet werden, oder um eine C-Datei auszusenden, die Objekte für die Befehlssymbole enthält.

 Die Schalter -D und -I haben die Syntax der Cl.exe C-Präprozessorflags, die denselben Namen haben. -D-Definitionen mit dem Format X=Y werden für \<die Erweiterung `Condition` von XML-basierten definierten> Tests in Attributen verwendet. -Ich include Pfade werden \<verwendet, \<um \<Include>, Extern> und Bitmap> Dateireferenzen aufzulösen. Weitere Informationen finden Sie in der [VSCT XML Schema Referenz](../../extensibility/vsct-xml-schema-reference.md).

 Der VSCT-Compiler kann auch eine zuvor erstellte Binärdatei dekompilieren. Geben Sie dazu eine Binärdatei \<für die infile>.   Wenn die Binärdatei vom VSCT-Compiler erstellt wurde, hat sie ihre Symbole bereits \<eingebettet und erzeugt ausgabegemäß mit den symbolischen Namen in einem> Abschnitt der Ausgabe. Wenn die Binärdatei vom CTC-Compiler erstellt wurde, enthält die Ausgabe die eigentlichen GUIDs und IDs. Wenn sich die *.ctsym-Datei, die von aktuellen Versionen von Ctc.exe erstellt wird, im selben Ordner wie die binäre Eingabedatei befindet, werden die Symbole aus dieser Datei geladen und für die Ausgabe verwendet.

## <a name="see-also"></a>Weitere Informationen
- [VSCT-Dateien (Visual Studio Command Table)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)
- [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
