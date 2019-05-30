---
title: Anatomie eines VSIX-Pakets | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8f0b748e80726d69e5b826982596a0a32675bd7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352278"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomie eines VSIX-Pakets
Ein VSIX-Paket ist eine *VSIX* Datei, die eine oder mehrere Visual Studio-Erweiterungen zusammen mit den Metadaten von Visual Studio enthält verwendet wird, zu klassifizieren und die Erweiterungen installieren. Diese Metadaten enthalten ist im VSIX-Manifest und die *[Content_Types] .xml* Datei. Ein VSIX-Paket kann auch enthalten, eine oder mehrere *Extension.vsixlangpack* Dateien zu setuptext lokalisiert, und können zusätzliche VSIX-Pakete, um Abhängigkeiten zu installieren.

 VSIX-Paketformat folgt den Open Packaging Conventions (OPC) Standard. Das Paket enthält die Binärdateien und die unterstützenden Dateien, zusammen mit einem *[Content_Types] .xml* Datei und ein *VSIX* manifest-Datei. Ein VSIX-Paket kann die Ausgabe von mehreren Projekten oder sogar mehrere Pakete, die ihre eigenen Manifeste umfassen, enthalten.

> [!NOTE]
> Die Namen der Dateien in VSIX-Pakete enthalten, darf keine Leerzeichen enthalten, noch in Uniform Resource Identifiers (URI), als reservierten Zeichen definierte [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).

## <a name="the-vsix-manifest"></a>Das VSIX-manifest
 Das VSIX-Manifest enthält Informationen über die zu installierende Erweiterung und folgt dem VSX-Schema. Weitere Informationen finden Sie unter [Referenz zum VSIX-Erweiterung Schema 1.0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Eine Beispiel-VSIX-Manifests finden Sie unter [PackageManifest-Element (Stammelement, VSX-Schema)](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187).

 Das VSIX-Manifest muss den Namen `extension.vsixmanifest` beim in enthalten ist ein ^ VSIX *-Datei.

## <a name="the-content"></a>Der Inhalt
 Vorlagen, Toolboxelemente auswählen, VSPackages oder eine andere Art von Erweiterung, die von Visual Studio unterstützt wird, kann ein VSIX-Paket enthalten.

## <a name="language-packs"></a>Language Packs
 Ein VSIX-Paket kann einmal oder mehrmals enthalten *Extension.vsixlangpack* Dateien lokalisierten Text während der Installation bereitstellen. Weitere Informationen finden Sie unter [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md).

## <a name="dependencies-and-references"></a>Abhängigkeiten und Verweise
 Ein VSIX-Paket möglicherweise andere VSIX-Pakete als Verweise enthalten. Jedes dieser anderen Pakete muss einen eigenen VSIX-Manifest enthalten.

 Wenn ein Benutzer versucht, eine Erweiterung zu installieren, die Abhängigkeiten enthält, überprüft das Installationsprogramm an, dass die erforderlichen Assemblys auf dem System des Benutzers installiert werden. Wenn die erforderlichen Assemblys nicht gefunden werden, **Erweiterungen und Updates** zeigt eine Liste der fehlenden Assemblys.

 Wenn das Erweiterungsmanifest, eine oder mehrere enthält [Verweis](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) Elemente **Erweiterungen und Updates** vergleicht das Manifest der jeder Verweis auf die Erweiterungen, die auf dem System installiert sind, und installiert die Erweiterung verwiesen, wenn es nicht bereits installiert ist. Wenn eine frühere Version einer Erweiterung auf die verwiesen wird, installiert ist, wird Sie durch die neuere Version ersetzt.

 Wenn ein Projekt in einer Projektmappe mit mehreren Projekten einen Verweis auf ein anderes Projekt in der gleichen Projektmappe enthält, enthält das VSIX-Paket der Abhängigkeiten von diesem Projekt an. Sie können dieses Verhalten überschreiben, indem Sie auf den Verweis für das interne-Projekt, und klicken Sie dann in der **Eigenschaften** Fenster Festlegen der **Ausgabe eingeschlossene Gruppen in VSIX-Datei** Eigenschaft `BuiltProjectOutputGroup`.

 Um Satelliten-DLLs aus referenzierten Assemblys im VSIX-Paket einzuschließen, fügen `SatelliteDllsProjectOutputGroup` auf die **Ausgabe eingeschlossene Gruppen in VSIX-Datei** Eigenschaft.

## <a name="installation-location"></a>Installationspfad
 Während der Installation **Erweiterungen und Updates** sucht nach den Inhalt des VSIX-Paket in einem Ordner unter *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions*.

 Standardmäßig gilt die Installation nur für den aktuellen Benutzer, da *%LocalAppData%* ist ein Verzeichnis für benutzerspezifische. Allerdings setzen Sie die [AllUsers](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) Element des Manifests, das `True`, wird die Erweiterung installiert werden, unter <em>... \\</em> VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> werden für alle Benutzer des Computers zur Verfügung stehen.

## <a name="contenttypesxml"></a>[Content_Types].xml
 Die *[Content_Types] .xml* Datei identifiziert die Dateitypen in der erweiterten *VSIX* Datei. Visual Studio verwendet diese Datei während der Installation des Pakets, aber die Datei selbst wird nicht installiert. Weitere Informationen zu dieser Datei finden Sie unter [die Struktur der [Content_types] .xml-Datei](the-structure-of-the-content-types-dot-xml-file.md).

 Ein *[Content_Types] .xml* Datei ist durch den Open Packaging Conventions (OPC) Standard erforderlich. Weitere Informationen zu OPC finden Sie unter [OPC: Ein neuer Standard für das Verpacken Ihrer Daten](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) auf der MSDN-Website.