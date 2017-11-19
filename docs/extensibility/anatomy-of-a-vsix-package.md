---
title: Aufbau eines VSIX-Pakets | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 519993c8527b0cd64c283416cd60eb48112e6886
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="anatomy-of-a-vsix-package"></a>Aufbau eines VSIX-Pakets
Ein VSIX-Paket ist eine VSIX-Datei, die eine oder mehrere Visual Studio-Erweiterungen, zusammen mit den Metadaten enthält, die Visual Studio zum Klassifizieren und Installieren der Erweiterungen verwendet. Diese Metadaten sind im VSIX-Manifest und die [Content_Types] .xml-Datei enthalten. Ein VSIX-Paket kann auch eine oder mehrere Extension.vsixlangpack-Dateien zum Bereitstellen von lokalisierten Setup Text enthalten und kann zusätzliche VSIX-Pakete zum Installieren von Abhängigkeiten enthalten.  
  
 VSIX-Paketformat folgt den Standard (Open Packaging Conventions, OPC). Das Paket enthält die Binärdateien und unterstützende Dateien, sowie eine [Content_Types] .xml-Datei und ein VSIX-Datei manifest. Ein VSIX-Paket kann die Ausgabe von mehreren Projekten oder auch mehrere Pakete mit ihren eigenen Manifeste enthalten.  
  
> [!NOTE]
>  Die Namen der Dateien, die in VSIX-Pakete enthalten, darf keine Leerzeichen enthalten, noch in Uniform Resource Identifiers (URI), als reservierten Zeichen definiert, unter [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>Das VSIX-Manifest  
 Das VSIX-Manifest enthält Informationen über die Erweiterung zu installierenden und folgt dem VSX-Schema. Weitere Informationen finden Sie unter [VSIX-Erweiterung Schemareferenz 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Ein Beispiel für ein VSIX-Manifest finden Sie unter [PackageManifest-Element (Stammelement, VSX-Schema)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 Das VSIX-Manifest muss den Namen `extension.vsixmanifest` Wenn sie in eine VSIX-Datei enthalten ist.  
  
## <a name="the-content"></a>Der Inhalt  
 Vorlagen, Toolboxelemente, VSPackages oder eine beliebige andere Art von Erweiterung, die von Visual Studio unterstützt wird, kann ein VSIX-Paket enthalten.  
  
## <a name="language-packs"></a>Sprachpakete  
 Ein VSIX-Paket möglicherweise einmal oder mehrere Extension.vsixlangpack-Dateien zum Bereitstellen von lokalisierten Texts während der Installation enthalten. Weitere Informationen finden Sie unter [VSIX-Pakete zum Lokalisieren von](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Abhängigkeiten und Verweise  
 Ein VSIX-Paket möglicherweise andere VSIX-Pakete als Verweise enthalten. Jede dieser anderen Pakete muss einen eigenen VSIX-Manifest enthalten.  
  
 Wenn ein Benutzer versucht, eine Erweiterung zu installieren, die Abhängigkeiten enthält, wird vom Installationsprogramm überprüft, dass die erforderlichen Assemblys auf dem Benutzersystem installiert sind. Wenn die erforderlichen Assemblys nicht gefunden werden, **Erweiterungen und Updates** zeigt eine Liste der fehlenden Assemblys.  
  
 Das Erweiterungsmanifest enthält eine oder mehrere [Verweis](http://msdn.microsoft.com/en-us/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) Elemente **Erweiterungen und Updates** vergleicht das Manifest der jeder Verweis auf die Erweiterungen, die auf dem System installiert sind und installiert die Erweiterung verwiesen, wenn es nicht bereits installiert ist. Wenn eine frühere Version der Erweiterung auf die verwiesen wird, installiert ist, wird Sie durch die neuere Version ersetzt.  
  
 Wenn ein Projekt in einer Projektmappe mit mehreren Projekten einen Verweis auf ein anderes Projekt in der gleichen Projektmappe enthält, umfasst das VSIX-Paket die Abhängigkeiten von diesem Projekt an. Sie können dieses Verhalten überschreiben, indem Sie auf den Verweis für das interne-Projekt, klicken Sie dann in der **Eigenschaften** Fenster Festlegen der **Ausgabe VSIX umfasst Gruppen** Eigenschaft `BuiltProjectOutputGroup`.  
  
 Wenn Satelliten-DLLs aus referenzierten Assemblys im VSIX-Paket einschließen möchten, fügen `SatelliteDllsProjectOutputGroup` auf die **Ausgabe VSIX umfasst Gruppen** Eigenschaft.  
  
## <a name="installation-location"></a>Installationsspeicherort  
 Während der Installation **Erweiterungen und Updates** für den Inhalt des VSIX-Paket in einem Ordner unter % LocalAppData%\Microsoft\VisualStudio\14.0\Extensions sucht.  
  
 Standardmäßig gilt die Installation nur für den aktuellen Benutzer, da %LocalAppData% einen benutzerspezifischen-Verzeichnis ist. Jedoch wenn Sie festlegen, die ["ALLUSERS"](http://msdn.microsoft.com/en-us/ac817f50-3276-4ddb-b467-8bbb1432455b) Element des Manifests, um `True`, die Erweiterung wird unter installiert werden... \\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions und wird für alle Benutzer des Computers verfügbar sein.  
  
## <a name="contenttypesxml"></a>[Content_Types] .xml  
 [Content_Types] .xml-Datei identifiziert die Dateitypen in der erweiterten VSIX-Datei. Visual Studio verwendet diese Datei während der Installation des Pakets jedoch die Datei selbst wird nicht installiert. Weitere Informationen zu dieser Datei finden Sie unter [Struktur der [Content_types] .xml-Datei](the-structure-of-the-content-types-dot-xml-file.md).  
  
 Eine [Content_Types] .xml-Datei ist durch die Konventionen OPC (Open Packaging) standard erforderlich. Weitere Informationen zu OPC finden Sie unter [OPC: A New Standard für Verpackung Your Data](http://go.microsoft.com/fwlink/?LinkID=148207) auf der MSDN-Website.