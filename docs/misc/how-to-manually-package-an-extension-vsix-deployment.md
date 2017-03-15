---
title: "Gewusst wie: Manuelles Verpacken einer Erweiterung (VSIX-Bereitstellung) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d25990e0-e782-4a79-9d9a-1caf3c56c6a2
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# Gewusst wie: Manuelles Verpacken einer Erweiterung (VSIX-Bereitstellung)
Sie können ein VSIX\-Paket erstellen, um eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Erweiterung für die Bereitstellung zu verpacken. Es gibt drei Möglichkeiten zum Erstellen des Pakets:  
  
-   Erstellen Sie mithilfe einer der Erweiterungsvorlagen, die im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK enthalten sind, ein VSIX\-Paketprojekt. Dies ist die einfachste Möglichkeit für die meisten Szenarien.  
  
-   Packen Sie die Ausgabe des Erweiterungsprojekts in ein leeres [VSIX\-Projekt](../extensibility/vsix-project-template.md). Wir empfehlen diese Option für Vorlagen, nicht unterstützte Assemblys und benutzerdefinierte Typen.  
  
-   Erstellen Sie manuell ein VSIX\-Paket. Diese Option wird nur dann empfohlen,  wenn die beiden anderen Optionen nicht verfügbar sind.  
  
 In diesem Dokument wird die dritte Option erläutert:  
  
## Erstellen eines VSIX\-Pakets  
 Um eine Erweiterung manuell zu verpacken, fügen Sie dem Erweiterungsprojekt eine extension.manifest\- und eine \[Content\_Types\].xml\-Datei hinzu, fassen Sie diese mit der Buildausgabe in einer komprimierten Datei zusammen, und benennen Sie die komprimierte Datei so um, dass sie die Dateierweiterung ".vsix" hat. Die zu verpackende Erweiterung muss einen Typ aufweisen, der vom [VSIX\-Schema](http://msdn.microsoft.com/de-de/76e410ec-b1fb-4652-ac98-4a4c52e09a2b) unterstützt wird.  
  
> [!NOTE]
>  Die Namen der Dateien in VSIX\-Paketen dürfen weder Leerzeichen noch in Uniform Resource Identifiers \(URI\) reservierte Zeichen enthalten, wie unter [\[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339) definiert.  
  
#### So erstellen Sie manuell ein VSIX\-Paket  
  
1.  Erstellen Sie eine Visual Studio\-Erweiterung eines Typs, der vom VSIX\-Schema unterstützt wird.  
  
2.  Erstellen Sie eine XML\-Datei, und nennen Sie sie `extension.vsixmanifest`.  
  
3.  Füllen Sie die Datei "extension.vsixmanifest" gemäß dem VSIX\-Schema. Ein Beispiel für ein Manifest finden Sie unter [PackageManifest\-Element \(Stammelement, VSX\-Schema\)](http://msdn.microsoft.com/de-de/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
4.  Erstellen Sie eine zweite XML\-Datei, und nennen Sie sie `[Content_Types].xml`.  
  
5.  Füllen Sie die Datei "\[Content\_Types\].xml" wie in [Die Struktur der Content\_types\] .xml\-Datei](../Topic/The%20Structure%20of%20the%20Content_types].xml%20File.md) definiert.  
  
6.  Fügen Sie beide XML\-Dateien zusammen mit der zu bereitstellenden Erweiterung in ein Verzeichnis ein.  
  
     Speichern Sie bei einer Projektvorlage oder Elementvorlage die ZIP\-Datei, die die Vorlage enthält, im selben Ordner wie die XML\-Dateien. Fügen Sie die XML\-Dateien nicht der ZIP\-Datei hinzu.  
  
     In allen anderen Fällen müssen sich die XML\-Dateien im selben Verzeichnis wie die Buildausgabe befinden.  
  
7.  Klicken Sie in Windows\-Explorer mit der Maustaste auf den Ordner, der den Erweiterungsinhalt und die beiden XML\-Dateien enthält, klicken Sie auf **Senden an**, und klicken Sie dann auf **Komprimierten \(gezippten\) Ordner**.  
  
8.  Benennen Sie die resultierende ZIP\-Datei in *Dateiname*.vsix um, wobei *Dateiname* der Name der verteilbaren Datei ist, mit der das Paket installiert wird.  
  
## Siehe auch  
 [Lieferung von Visual Studio\-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)   
 [Anatomie eines VSIX\-Pakets](../extensibility/anatomy-of-a-vsix-package.md)   
 [PackageManifest\-Element \(Stammelement, VSX\-Schema\)](http://msdn.microsoft.com/de-de/f8ae42ba-775a-4d2b-976a-f556e147f187)