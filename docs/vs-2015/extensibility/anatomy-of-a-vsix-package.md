---
title: Anatomie eines VSIX-Pakets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 645d9bff0b1f1bd3ac3afe3f5c815d9b9cd208d3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514958"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomie eines VSIX-Pakets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Anatomie eines VSIX-Pakets](https://docs.microsoft.com/visualstudio/extensibility/anatomy-of-a-vsix-package).  
  
Ein VSIX-Paket ist eine VSIX-Datei, die eine oder mehrere Visual Studio-Erweiterungen zusammen mit den Metadaten, die Visual Studio verwendet wird enthält, zu klassifizieren und die Erweiterungen installieren. Diese Metadaten sind in VSIX-Manifest, und der [Content_Types] .xml-Datei enthalten. Ein VSIX-Paket kann auch eine oder mehrere Extension.vsixlangpack-Dateien zum Bereitstellen von lokalisierten Text enthalten, und eventuell weitere VSIX-Pakete, um Abhängigkeiten zu installieren.  
  
 VSIX-Paketformat folgt den Open Packaging Conventions (OPC) Standard. Das Paket enthält die Binärdateien und die unterstützenden Dateien, sowie eine [Content_Types] .xml-Datei und ein VSIX-Manifestdatei. Ein VSIX-Paket kann die Ausgabe von mehreren Projekten oder sogar mehrere Pakete, die ihre eigenen Manifeste umfassen, enthalten.  
  
> [!NOTE]
>  Die Namen der Dateien in VSIX-Pakete enthalten, darf keine Leerzeichen enthalten, noch in Uniform Resource Identifiers (URI), als reservierten Zeichen definierte [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>Das VSIX-Manifest  
 Das VSIX-Manifest enthält Informationen über die zu installierende Erweiterung und folgt dem VSX-Schema. Weitere Informationen finden Sie unter [Referenz zum VSIX-Erweiterungsschema 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Eine Beispiel-VSIX-Manifests finden Sie unter [PackageManifest-Element (Stammelement, VSX-Schema)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 Das VSIX-Manifest muss den Namen `extension.vsixmanifest` Wenn sie in einer VSIX-Datei enthalten ist.  
  
## <a name="the-content"></a>Der Inhalt  
 Vorlagen, Toolboxelemente auswählen, VSPackages oder eine andere Art von Erweiterung, die von Visual Studio unterstützt wird, kann ein VSIX-Paket enthalten.  
  
## <a name="language-packs"></a>Sprachpakete  
 Ein VSIX-Paket kann einmal oder mehrere Extension.vsixlangpack-Dateien während der Installation lokalisierter Text zu enthalten. Weitere Informationen finden Sie unter [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Abhängigkeiten und Verweise  
 Ein VSIX-Paket möglicherweise andere VSIX-Pakete als Verweise enthalten. Jedes dieser anderen Pakete muss einen eigenen VSIX-Manifest enthalten.  
  
 Wenn ein Benutzer versucht, eine Erweiterung zu installieren, die Abhängigkeiten enthält, überprüft das Installationsprogramm an, dass die erforderlichen Assemblys auf dem System des Benutzers installiert werden. Wenn die erforderlichen Assemblys nicht gefunden werden, **Erweiterungen und Updates** zeigt eine Liste der fehlenden Assemblys.  
  
 Wenn das Erweiterungsmanifest, eine oder mehrere enthält [Verweis](http://msdn.microsoft.com/en-us/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) Elemente **Erweiterungen und Updates** vergleicht das Manifest der jeder Verweis auf die Erweiterungen, die auf dem System installiert sind, und installiert die Erweiterung verwiesen, wenn es nicht bereits installiert ist. Wenn eine frühere Version einer Erweiterung auf die verwiesen wird, installiert ist, wird Sie durch die neuere Version ersetzt.  
  
 Wenn ein Projekt in einer Projektmappe mit mehreren Projekten einen Verweis auf ein anderes Projekt in der gleichen Projektmappe enthält, enthält das VSIX-Paket der Abhängigkeiten von diesem Projekt an. Sie können dieses Verhalten überschreiben, indem Sie auf den Verweis für das interne-Projekt, und klicken Sie dann in der **Eigenschaften** Fenster Festlegen der **Ausgabe eingeschlossene Gruppen in VSIX-Datei** Eigenschaft `BuiltProjectOutputGroup`.  
  
 Um Satelliten-DLLs aus referenzierten Assemblys im VSIX-Paket einzuschließen, fügen `SatelliteDllsProjectOutputGroup` auf die **Ausgabe eingeschlossene Gruppen in VSIX-Datei** Eigenschaft.  
  
## <a name="installation-location"></a>Installationsspeicherort  
 Während der Installation **Erweiterungen und Updates** für den Inhalt des VSIX-Paket in einem Ordner unter % LocalAppData%\Microsoft\VisualStudio\14.0\Extensions aussieht.  
  
 Standardmäßig wird die Installation nur für den aktuellen Benutzer angewendet, da % LocalAppData% ein benutzerspezifisches ist. Allerdings setzen Sie die [AllUsers](http://msdn.microsoft.com/en-us/ac817f50-3276-4ddb-b467-8bbb1432455b) Element des Manifests, das `True`, unter die Erweiterung installiert werden... \\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions werden für alle Benutzer des Computers zur Verfügung stehen.  
  
## <a name="contenttypesxml"></a>[Content_Types] .xml  
 Die [Content_Types] .xml-Datei identifiziert die Dateitypen in der erweiterten VSIX-Datei. Visual Studio verwendet diese Datei während der Installation des Pakets, aber die Datei selbst wird nicht installiert. Weitere Informationen zu dieser Datei finden Sie unter [Struktur der Content_types\]XML-Datei](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
 Eine [Content_Types] .xml-Datei ist durch den OPC Open Packaging Conventions () standard erforderlich. Weitere Informationen zu OPC finden Sie unter [OPC: A New Standard für die Paketerstellung Your Data](http://go.microsoft.com/fwlink/?LinkID=148207) auf der MSDN-Website.

