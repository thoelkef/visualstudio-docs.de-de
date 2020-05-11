---
title: Anatomie eines VSIX-Pakets | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a6d3f994c531bd36ab4281c5f0b27e993cd3392
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740096"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomie eines VSIX-Pakets
Ein VSIX-Paket ist eine *VSIX-Datei,* die eine oder mehrere Visual Studio-Erweiterungen enthält, zusammen mit den Metadaten, die Visual Studio zum Klassifizieren und Installieren der Erweiterungen verwendet. Diese Metadaten sind im VSIX-Manifest und in der Datei *[Content_Types].xml* enthalten. Ein VSIX-Paket kann auch eine oder mehrere *Extension.vsixlangpack-Dateien* enthalten, um lokalisierten Setuptext bereitzustellen, und möglicherweise zusätzliche VSIX-Pakete zum Installieren von Abhängigkeiten enthalten.

 Das VSIX-Paketformat folgt dem Open Packaging Conventions (OPC)-Standard. Das Paket enthält Binärdateien und unterstützende Dateien sowie eine *[Content_Types].xml-Datei* und eine *.vsix-Manifestdatei.* Ein VSIX-Paket kann die Ausgabe mehrerer Projekte oder sogar mehrerer Pakete enthalten, die eigene Manifeste haben.

> [!NOTE]
> Die Namen der in VSIX-Paketen enthaltenen Dateien dürfen keine Leerzeichen oder Zeichen enthalten, die in Uniform Resource Identifiers (URI) reserviert sind, wie unter [ \[RFC2396\]](https://www.rfc-editor.org/rfc/rfc2396.txt)definiert.

## <a name="the-vsix-manifest"></a>Das VSIX-Manifest
 Das VSIX-Manifest enthält Informationen über die zu installierende Erweiterung und folgt dem VSX-Schema. Weitere Informationen finden Sie unter [VSIX-Erweiterungsschema 1.0-Referenz](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Ein Beispiel vSIX-Manifest finden Sie unter [PackageManifest-Element (root-Element, VSX-Schema)](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187).

 Das VSIX-Manifest `extension.vsixmanifest` muss benannt werden, wenn es in einer Datei mit dem Namen .vsix* enthalten ist.

## <a name="the-content"></a>der Inhalt
 Ein VSIX-Paket kann Vorlagen, Toolboxelemente, VSPackages oder jede andere Art von Erweiterung enthalten, die von Visual Studio unterstützt wird.

## <a name="language-packs"></a>Language Packs
 Ein VSIX-Paket kann ein oder mehr *Extension.vsixlangpack-Dateien* enthalten, um lokalisierten Text während der Installation bereitzustellen. Weitere Informationen finden Sie unter [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md).

## <a name="dependencies-and-references"></a>Abhängigkeiten und Referenzen
 Ein VSIX-Paket kann andere VSIX-Pakete als Referenzen enthalten. Jedes dieser anderen Pakete muss ein eigenes VSIX-Manifest enthalten.

 Wenn ein Benutzer versucht, eine Erweiterung mit Abhängigkeiten zu installieren, überprüft das Installationsprogramm, ob die erforderlichen Assemblys auf dem Benutzersystem installiert sind. Wenn die erforderlichen Assemblys nicht gefunden werden, zeigt **Extensions and Updates** eine Liste der fehlenden Assemblys an.

 Wenn das Erweiterungsmanifest ein oder mehrere [Referenzelemente](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) enthält, vergleicht **Extensions and Updates** das Manifest jedes Verweises mit den Erweiterungen, die auf dem System installiert sind, und installiert die referenzierte Erweiterung, wenn sie nicht bereits installiert ist. Wenn eine frühere Version einer referenzierten Erweiterung installiert ist, ersetzt sie durch die neuere Version.

 Wenn ein Projekt in einer Projektmappe mit mehreren Projekten einen Verweis auf ein anderes Projekt in derselben Projektmappe enthält, enthält das VSIX-Paket die Abhängigkeiten dieses Projekts. Sie können dieses Verhalten überschreiben, indem Sie auf die Referenz für das interne Projekt klicken und `BuiltProjectOutputGroup`dann im Fenster **Eigenschaften** die in der **VSIX-Eigenschaft enthaltenen Ausgabegruppen** auf festlegen.

 Um Satelliten-DLLs aus Assemblys, auf die `SatelliteDllsProjectOutputGroup` verwiesen wird, in das VSIX-Paket einzuschließen, fügen Sie die in der **VSIX-Eigenschaft enthaltene Ausgabegruppen** hinzu.

## <a name="installation-location"></a>Installationspfad
 Während der Installation sucht **Extensions and Updates** nach dem Inhalt des VSIX-Pakets in einem Ordner unter *%LocalAppData%-Microsoft-VisualStudio-Erweiterungen*.

 Standardmäßig gilt die Installation nur für den aktuellen Benutzer, da *%LocalAppData%* ein benutzerspezifisches Verzeichnis ist. Wenn Sie jedoch das [AllUsers-Element](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) `True`des Manifests auf festlegen, wird die Erweiterung unter <em>installiert. \\ </em>VisualStudioInstallationFolder<em>, Common7, IDE, Erweiterungen</em> und steht allen Benutzern des Computers zur Verfügung.

## <a name="content_typesxml"></a>[Content_Types].xml
 Die Datei *[Content_Types].xml* identifiziert die Dateitypen in der erweiterten *.vsix-Datei.* Visual Studio verwendet diese Datei während der Installation des Pakets, installiert die Datei jedoch nicht selbst. Weitere Informationen zu dieser Datei finden Sie unter [Die Struktur der Datei [Content_types].xml](the-structure-of-the-content-types-dot-xml-file.md).

 Eine *[Content_Types].xml-Datei* ist nach dem Open Packaging Conventions (OPC)-Standard erforderlich. Weitere Informationen zu OPC finden Sie unter [OPC: Ein neuer Standard für](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) das Verpacken Ihrer Daten auf der MSDN-Website.
