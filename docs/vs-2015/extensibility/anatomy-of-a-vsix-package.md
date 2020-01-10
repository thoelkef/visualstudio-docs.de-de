---
title: Anatomie eines VSIX-Pakets | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2a769b0d04f76a2a32c00e262ff03b400af02feb
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852286"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomie eines VSIX-Pakets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bei einem VSIX-Paket handelt es sich um eine VSIX-Datei, die eine oder mehrere Visual Studio-Erweiterungen enthält, sowie die Metadaten, die Visual Studio zum klassifizieren und Installieren der Erweiterungen verwendet. Diese Metadaten sind im VSIX-Manifest und in der Datei [Content_Types]. XML enthalten. Ein VSIX-Paket kann auch eine oder mehrere Extension. vsixlangpack-Dateien enthalten, um lokalisierten Setup Text bereitzustellen, und kann weitere VSIX-Pakete enthalten, um Abhängigkeiten zu installieren.  
  
 Das VSIX-Paketformat folgt dem OPC-Standard (Open Packaging Conventions). Das Paket enthält Binärdateien und unterstützende Dateien sowie eine [Content_Types]. XML-Datei und eine VSIX-Manifest-Datei. Ein VSIX-Paket kann die Ausgabe mehrerer Projekte oder sogar mehrerer Pakete enthalten, die eigene Manifeste enthalten.  
  
> [!NOTE]
> Die Namen der Dateien, die in VSIX-Paketen enthalten sind, dürfen keine Leerzeichen und keine Zeichen enthalten, die in URI (Uniform Resource Identifier) reserviert sind, wie unter [\[rfc2396\]](https://go.microsoft.com/fwlink/?LinkId=90339)definiert.  
  
## <a name="the-vsix-manifest"></a>Das VSIX-Manifest  
 Das VSIX-Manifest enthält Informationen über die zu installierende Erweiterung und folgt dem VSX-Schema. Weitere Informationen finden Sie in der [Referenz zum VSIX-Erweiterungs Schema 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Ein Beispiel für ein VSIX-Manifest finden Sie unter [packagemanifest-Element (Stamm Element, VSX-Schema)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 Das VSIX-Manifest muss `extension.vsixmanifest` benannt werden, wenn es in einer vsix-Datei enthalten ist.  
  
## <a name="the-content"></a>Der Inhalt  
 Ein VSIX-Paket kann Vorlagen, Toolbox Elemente, VSPackages oder eine beliebige andere Art von Erweiterung enthalten, die von Visual Studio unterstützt wird.  
  
## <a name="language-packs"></a>Sprachpakete  
 Ein VSIX-Paket kann eine oder mehrere Extension. vsixlangpack-Dateien enthalten, um lokalisierten Text während der Installation bereitzustellen. Weitere Informationen finden Sie unter [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Abhängigkeiten und Verweise  
 Ein VSIX-Paket kann andere VSIX-Pakete als Verweise enthalten. Jedes dieser anderen Pakete muss ein eigenes VSIX-Manifest enthalten.  
  
 Wenn ein Benutzer versucht, eine Erweiterung zu installieren, die Abhängigkeiten aufweist, wird vom Installationsprogramm überprüft, ob die erforderlichen Assemblys auf dem Benutzersystem installiert sind. Wenn die erforderlichen Assemblys nicht gefunden werden, wird in **Erweiterungen und Updates** eine Liste der fehlenden Assemblys angezeigt.  
  
 Wenn das Erweiterungs Manifest ein oder mehrere [Verweis](https://msdn.microsoft.com/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) Elemente enthält, vergleicht **Erweiterungen und Updates** das Manifest jedes Verweises mit den Erweiterungen, die auf dem System installiert sind, und installiert die referenzierte Erweiterung, wenn Sie nicht bereits installiert ist. Wenn eine frühere Version einer Erweiterung installiert ist, auf die verwiesen wird, ersetzt Sie die neuere Version.  
  
 Wenn ein Projekt in einer Projekt Mappe mit mehreren Projekten einen Verweis auf ein anderes Projekt in der gleichen Projekt Mappe enthält, enthält das VSIX-Paket die Abhängigkeiten des Projekts. Sie können dieses Verhalten überschreiben, indem Sie auf den Verweis für das interne Projekt klicken und dann im **Eigenschaften** Fenster die **in der VSIX-Eigenschaft enthaltenen Ausgabe Gruppen** auf `BuiltProjectOutputGroup`festlegen.  
  
 Um Satelliten-DLLs aus referenzierten Assemblys im VSIX-Paket einzuschließen, fügen Sie `SatelliteDllsProjectOutputGroup` den **in der VSIX-Eigenschaft enthaltenen Ausgabe Gruppen** hinzu.  
  
## <a name="installation-location"></a>Installationspfad  
 Bei der Installation wird durch **Erweiterungen und Updates** nach dem Inhalt des VSIX-Pakets in einem Ordner unter "%LocalAppData%\microsoft\visualstudio\14.0\Extensions" gesucht.  
  
 Standardmäßig gilt die Installation nur für den aktuellen Benutzer, da% LocalAppData% ein benutzerspezifisches Verzeichnis ist. Wenn Sie jedoch das [ALLUSERS](https://msdn.microsoft.com/ac817f50-3276-4ddb-b467-8bbb1432455b) -Element des Manifests auf `True`festlegen, wird die Erweiterung unter installiert.\\*visualstudioinstallationfolder*\common7\ide\Extensions und steht allen Benutzern des Computers zur Verfügung.  
  
## <a name="content_typesxml"></a>[Content_Types]. XML  
 Die Datei [Content_Types]. XML identifiziert die Dateitypen in der erweiterten vsix-Datei. Visual Studio verwendet diese Datei bei der Installation des Pakets, installiert die Datei jedoch nicht selbst. Weitere Informationen zu dieser Datei finden Sie [in der Struktur der Datei "Content_Types\]. XML](../extensibility/the-structure-of-the-content-types-dot-xml-file.md)".  
  
 Eine [Content_Types]. XML-Datei wird vom OPC-Standard (Open Packaging Conventions) benötigt. Weitere Informationen zu OPC finden Sie unter [OPC: ein neuer Standard zum Verpacken Ihrer Daten](https://msdn.microsoft.com/magazine/cc163372.aspx) auf der MSDN-Website.
