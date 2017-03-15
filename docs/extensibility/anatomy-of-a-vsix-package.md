---
title: Anatomie eines VSIX-Pakets | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 7278fb37984b92a6a07823c552db5c59a446d0d2
ms.openlocfilehash: 633db03670180ac83c5c936f66953fb38d4ebd67
ms.lasthandoff: 02/22/2017

---
# <a name="anatomy-of-a-vsix-package"></a>Anatomie eines VSIX-Pakets
Ein VSIX-Paket ist eine VSIX-Datei, die eine oder mehrere Visual Studio-Erweiterungen zusammen mit den Metadaten, die Visual Studio verwendet wird enthält, zu klassifizieren und die Erweiterungen installieren. Diese Metadaten sind im VSIX-Manifest und die [Content_Types] .xml-Datei enthalten. Ein VSIX-Paket kann auch eine oder mehrere Extension.vsixlangpack-Dateien zum Bereitstellen von lokalisierten Setup-Text enthalten, und möglicherweise zusätzliche VSIX-Pakete, um Abhängigkeiten zu installieren.  
  
 VSIX-Paketformat folgt den Standard Open Packaging-Konventionen (OPC). Das Paket enthält die Binärdateien und unterstützende Dateien, zusammen mit einer [Content_Types] .xml-Datei und eine VSIX-Manifestdatei. Ein VSIX-Paket kann die Ausgabe mehrerer Projekte oder sogar mehrere Pakete mit ihren eigenen Manifeste enthalten.  
  
> [!NOTE]
>  Die Namen der Dateien in VSIX-Pakete enthalten darf keine Leerzeichen enthalten, noch in Uniform Resource Identifiers (URI), als reservierten Zeichen definiert, unter [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>Das VSIX-Manifest  
 Das VSIX-Manifest enthält Informationen über die Erweiterung installiert werden und folgt dem VSX-Schema. Weitere Informationen finden Sie unter [VSIX-Erweiterung Schemareferenz 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Ein Beispiel für ein VSIX-Manifest finden Sie unter [PackageManifest Element (Stammelement, VSX-Schema)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 Das VSIX-Manifest muss den Namen `extension.vsixmanifest` wenn er in einer VSIX-Datei enthalten ist.  
  
## <a name="the-content"></a>Der Inhalt  
 Vorlagen, Toolboxelemente, VSPackages oder eine andere Art von Erweiterung, die von Visual Studio unterstützt wird, kann ein VSIX-Paket enthalten.  
  
## <a name="language-packs"></a>Sprachpakete  
 Ein VSIX-Paket kann einmal oder mehrere Extension.vsixlangpack-Dateien während der Installation lokalisierten Text bereitstellen enthalten. Weitere Informationen finden Sie unter [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Abhängigkeiten und Verweise  
 Ein VSIX-Paket möglicherweise andere VSIX-Pakete als Verweise enthalten. Jedes der anderen Pakete muss einen eigenen VSIX-Manifest enthalten.  
  
 Wenn ein Benutzer versucht, eine Erweiterung zu installieren, die abhängig ist, wird vom Installationsprogramm überprüft, dass die erforderlichen Assemblys auf dem Benutzersystem installiert sind. Wenn die erforderlichen Assemblys nicht gefunden werden, **Erweiterungen und Updates** zeigt eine Liste der fehlenden Assemblys.  
  
 Das Erweiterungsmanifest enthält eine oder mehrere [Verweis](http://msdn.microsoft.com/en-us/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) Elemente **Erweiterungen und Updates** vergleicht das Manifest für alle Verweise auf die Erweiterungen, die auf dem System installiert sind und die referenzierte Erweiterung wird installiert, wenn es nicht bereits installiert ist. Wenn eine frühere Version der Erweiterung auf die verwiesen wird, installiert ist, wird Sie durch die neuere Version ersetzt.  
  
 Wenn ein Projekt in einer Projektmappe mit mehreren Projekten einen Verweis auf ein anderes Projekt in der gleichen Projektmappe enthält, enthält das VSIX-Paket die Abhängigkeiten des Projekts. Sie können dieses Verhalten überschreiben, indem Sie auf den Verweis für das interne-Projekt, und klicken Sie dann in der **Eigenschaften** Fenster Festlegen der **Ausgabe Gruppen enthalten, in VSIX** -Eigenschaft `BuiltProjectOutputGroup`.  
  
 Für die Einbeziehung der Satelliten-DLLs von referenzierten Assemblys im VSIX-Paket hinzufügen `SatelliteDllsProjectOutputGroup` an der **Ausgabe Gruppen enthalten, in VSIX** Eigenschaft.  
  
## <a name="installation-location"></a>Installationsspeicherort  
 Während der Installation **Erweiterungen und Updates** sieht für den Inhalt des VSIX-Paket in einem Ordner unter % LocalAppData%\Microsoft\VisualStudio\14.0\Extensions.  
  
 Standardmäßig gilt die Installation nur für den aktuellen Benutzer, da % LocalAppData% eine benutzerspezifische-Verzeichnis ist. Jedoch wenn Sie festlegen, die [AllUsers](http://msdn.microsoft.com/en-us/ac817f50-3276-4ddb-b467-8bbb1432455b) -Element des Manifests, das `True`, unter die Erweiterung installiert werden... \\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions und werden für alle Benutzer des Computers verfügbar sein.  
  
## <a name="contenttypesxml"></a>[Content_Types] .xml  
 Die [Content_Types] .xml-Datei identifiziert die Dateitypen in der erweiterten VSIX-Datei. Visual Studio verwendet diese Datei während der Installation des Pakets jedoch die Datei selbst wird nicht installiert. Weitere Informationen zu dieser Datei finden Sie unter [Struktur der [Content_types] .xml-Datei](the-structure-of-the-content-types-dot-xml-file.md).  
  
 Eine [Content_Types] .xml-Datei ist durch die Konventionen OPC (Open Packaging) standard erforderlich. Weitere Informationen zu OPC finden Sie unter [OPC: A New Standard für Verpackung Your Data](http://go.microsoft.com/fwlink/?LinkID=148207) auf der MSDN-Website.
