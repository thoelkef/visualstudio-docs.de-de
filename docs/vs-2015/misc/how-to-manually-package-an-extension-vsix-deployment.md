---
title: 'Vorgehensweise: Manuelles Verpacken einer Erweiterung (VSIX-Bereitstellung) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: d25990e0-e782-4a79-9d9a-1caf3c56c6a2
caps.latest.revision: 10
manager: jillfra
ms.openlocfilehash: a615aea75ec00e49ee4d2837b8b4e2b1d20d3306
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293626"
---
# <a name="how-to-manually-package-an-extension-vsix-deployment"></a>Gewusst wie: Manuelles Verpacken einer Erweiterung (VSIX-Bereitstellung)
Sie können ein VSIX-Paket erstellen, um eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Erweiterung für die Bereitstellung zu verpacken. Es gibt drei Möglichkeiten zum Erstellen des Pakets:  
  
- Erstellen Sie mithilfe einer der Erweiterungsvorlagen, die im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK enthalten sind, ein VSIX-Paketprojekt. Dies ist die einfachste Möglichkeit für die meisten Szenarien.  
  
- Packen Sie die Ausgabe des Erweiterungsprojekts in ein leeres [VSIX-Projekt](../extensibility/vsix-project-template.md). Wir empfehlen diese Option für Vorlagen, nicht unterstützte Assemblys und benutzerdefinierte Typen.  
  
- Erstellen Sie manuell ein VSIX-Paket. Diese Option wird nur dann empfohlen,  wenn die beiden anderen Optionen nicht verfügbar sind.  
  
  In diesem Dokument wird die dritte Option erläutert:  
  
## <a name="creating-a-vsix-package"></a>Erstellen eines VSIX-Pakets  
 Um eine Erweiterung manuell zu verpacken, fügen Sie dem Erweiterungsprojekt eine extension.manifest- und eine [Content_Types].xml-Datei hinzu, fassen Sie diese mit der Buildausgabe in einer komprimierten Datei zusammen, und benennen Sie die komprimierte Datei so um, dass sie die Dateierweiterung ".vsix" hat. Die zu verpackende Erweiterung muss einen Typ aufweisen, der vom [VSIX-Schema](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)unterstützt wird.  
  
> [!NOTE]
> Die Namen der Dateien in VSIX-Paketen dürfen keine Leerzeichen und keine Zeichen enthalten, die in URI (Uniform Resource Identifier) reserviert sind, wie unter [\[rfc2396\]](https://go.microsoft.com/fwlink/?LinkId=90339)definiert.  
  
#### <a name="to-manually-create-a-vsix-package"></a>So erstellen Sie manuell ein VSIX-Paket  
  
1. Erstellen Sie eine Visual Studio-Erweiterung eines Typs, der vom VSIX-Schema unterstützt wird.  
  
2. Erstellen Sie eine XML-Datei, und nennen Sie sie `extension.vsixmanifest`.  
  
3. Füllen Sie die Datei "extension.vsixmanifest" gemäß dem VSIX-Schema. Ein Beispiel für ein Manifest finden Sie unter [PackageManifest-Element (Stammelement, VSX-Schema)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
4. Erstellen Sie eine zweite XML-Datei, und nennen Sie sie `[Content_Types].xml`.  
  
5. Füllen Sie die Datei [Content_Types]. XML wie in [der Struktur der Content_Types\]. XML](../extensibility/the-structure-of-the-content-types-dot-xml-file.md)-Datei angegeben aus.  
  
6. Fügen Sie beide XML-Dateien zusammen mit der zu bereitstellenden Erweiterung in ein Verzeichnis ein.  
  
     Speichern Sie bei einer Projektvorlage oder Elementvorlage die ZIP-Datei, die die Vorlage enthält, im selben Ordner wie die XML-Dateien. Fügen Sie die XML-Dateien nicht der ZIP-Datei hinzu.  
  
     In allen anderen Fällen müssen sich die XML-Dateien im selben Verzeichnis wie die Buildausgabe befinden.  
  
7. Klicken Sie in Windows-Explorer mit der Maustaste auf den Ordner, der den Erweiterungsinhalt und die beiden XML-Dateien enthält, klicken Sie auf **Senden an**, und klicken Sie dann auf **Komprimierten (gezippten) Ordner**.  
  
8. Benennen Sie die resultierende ZIP-Datei in *Dateiname*.vsix um, wobei *Dateiname* der Name der verteilbaren Datei ist, mit der das Paket installiert wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Liefer  für Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)  
 [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)   
 [Packagemanifest-Element (Stamm Element, VSX-Schema)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187)