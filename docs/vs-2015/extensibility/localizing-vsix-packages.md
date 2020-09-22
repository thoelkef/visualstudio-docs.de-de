---
title: Lokalisieren von VSIX-Paketen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6143b21884bc92ac79ae0fd7292a11780fec4478
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840953"
---
# <a name="localizing-vsix-packages"></a>Lokalisieren von VSIX-Paketen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können ein VSIX-Paket lokalisieren, indem Sie für jede Zielsprache eine Erweiterung. vsixlangpack-Datei erstellen und diese dann in den richtigen Ordner einfügen. Wenn ein lokalisiertes Paket installiert wird, wird der lokalisierte Name der Erweiterung sowie eine lokalisierte Beschreibung angezeigt. Wenn Sie eine lokalisierte Lizenzdatei oder eine URL angeben, die auf lokalisierte Informationen verweist, werden diese ebenfalls angezeigt.  
  
 Wenn Ihr VSIX-Paket ein VSPackage enthält, das Menübefehle oder eine andere Benutzeroberfläche hinzufügt, finden Sie unter [Lokalisieren von Menübefehlen](../extensibility/localizing-menu-commands.md) Informationen zum Lokalisieren der neuen Benutzeroberflächen Elemente.  
  
## <a name="directory-structure"></a>Verzeichnisstruktur  
 Wenn ein Benutzer eine Erweiterung installiert, prüft **Extensions und Updates** die oberste Ebene des VSIX-Pakets auf einen Ordner, dessen Name mit dem Visual Studio-Gebiets Schema des Ziel Computers übereinstimmt. Wenn **Erweiterungen und Updates** eine vsixlangpack-Datei im Ordner finden, werden die lokalisierten Werte in dieser Datei durch die entsprechenden Werte in der vsixmanifest-Datei ersetzt. Diese Werte werden angezeigt, wenn die Erweiterung installiert wird. Das folgende Beispiel zeigt die Verzeichnisstruktur für ein VSIX-Paket, das in Spanisch (es-es) und Französisch (fr-FR) lokalisiert wird.  
  
 MyExtension.dll  
  
 Erweiterung. vsixmanifest  
  
 [Content_Types]. XML  
  
 es-ES  
  
 Erweiterung. vsixlangpack  
  
 fr-FR  
  
 Erweiterung. vsixlangpack  
  
> [!NOTE]
> Die von VSIX unterstützten Projektvorlagen in [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] generieren ein VSIX-Manifest und nennen es Source. Extension. vsixmanifest. Wenn das Projekt von Visual Studio erstellt wird, wird der Inhalt dieser Datei in das vsixmanifest-Erweiterungs Element im VSIX-Paket kopiert.  
  
## <a name="the-extensionvsixlangpack-file"></a>Die Dateierweiterung. vsixlangpack  
 Die Extension. vsixlangpack-Datei folgt dem [VSIX-Sprachpaket Schema](../extensibility/vsx-language-pack-schema-reference.md). Dieses Schema verfügt über ein [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) -Stamm Element und diese vier untergeordneten Elemente: [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [localizeddescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [MoreInfoUrl](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)und [License](../extensibility/license-element-vsix-language-pack-schema.md). Diese untergeordneten Elemente entsprechen den untergeordneten `Name` `Description` Elementen,, `MoreInfoURL` und `License` des- `Identifier` Elements der Extension. vsixmanifest-Datei.  
  
 Wenn Sie eine vsixlangpack-Datei erstellen, müssen Sie die- `Include in Vsix` Eigenschaft auf festlegen `true` . Andernfalls wird der lokalisierte Installations Text ignoriert.  
  
#### <a name="to-set-the-include-in-vsix-property"></a>So legen Sie die Eigenschaft in VSIX einschließen fest  
  
1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf die Dateierweiterung. vsixlangpack, und klicken Sie dann auf **Eigenschaften**.  
  
2. Klicken Sie im Eigenschaften Raster auf **in VSIX einschließen**, und legen Sie dessen Wert auf fest `true` .  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>BESCHREIBUNG  
 Das folgende Beispiel zeigt relevante Teile einer Erweiterung. vsixmanifest-Datei sowie die entsprechende Erweiterung. vsixlangpack-Datei für Spanisch. Die Werte aus dem Language Pack ersetzen die Werte aus dem Manifest, wenn das Visual Studio-Gebiets Schema des Ziel Computers auf Spanisch festgelegt ist.  
  
### <a name="code"></a>Code  
 [Extension. vsixmanifest]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VSIX ...>  
  <Identifier ...>  
    <Name>Family Tree</Name>  
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>  
    <License>EULA.rtf</License>  
    <MoreInfoURL>http://www.contoso.com/products/FamilyTree.htm</MoreInfoURL>  
    ...  
  </Identifier>  
  <References .../>  
  <Content .../>  
</VSIX>  
```  
  
 [Extension. vsixlangpack]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSIX languagepack-Element](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX-Projektvorlage](../extensibility/vsix-project-template.md)
