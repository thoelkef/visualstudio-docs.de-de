---
title: 'Vorgehensweise: Erstellen eines Paketmanifests | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 463286eb8360b728b3b7e3ce9396c9f4b7e11305
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-package-manifest"></a>Gewusst wie: Erstellen eines Paketmanifests
Um die erforderlichen Komponenten für Ihre Anwendung bereitstellen, können Sie ein Bootstrapperpaket verwenden. Ein Bootstrapperpaket enthält eine einzelne Produktmanifestdatei aber ein Paketmanifest für jedes Gebietsschema. Gemeinsam genutzte Funktionen in den verschiedenen lokalisierten Versionen sollte in das Produktmanifest wechseln.  
  
 Weitere Informationen zu Paketmanifesten, finden Sie unter [Vorgehensweise: Erstellen eines Produktmanifests](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="creating-the-package-manifest"></a>Erstellen das Paketmanifest  
  
#### <a name="to-create-the-package-manifest"></a>So erstellen das Paketmanifest  
  
1.  Erstellen Sie ein Verzeichnis für das Bootstrapperpaket. Dieses Beispiel verwendet die C:\package.  
  
2.  Erstellen Sie ein Unterverzeichnis mit dem Namen des Gebietsschemas, z. B. "En" für Englisch.  
  
3.  In Visual Studio, erstellen Sie eine XML-Datei mit dem Namen `package.xml`, und speichern sie den Ordner "C:\package\en".  
  
4.  Fügen Sie XML-Code, um den Namen des Bootstrapper-Pakets, das die Kultur für dieses lokalisierte Paketmanifest und den optionalen Lizenzvertrag aufzulisten. Die folgende XML-Code verwendet die Variablen `DisplayName` und `Culture`, die in einem späteren Element definiert werden.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Hinzufügen von XML, um alle Dateien aufgelistet, die im Verzeichnis gebietsschemaspezifische sind. Die folgende XML-Code verwendet eine Datei mit dem Namen eula.txt, die für anwendbar ist die **En** Gebietsschema.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Fügen Sie XML-Code, um lokalisierbare Zeichenfolgen für das Bootstrapperpaket zu definieren. Die folgende XML-Code fügt Fehlerzeichenfolgen für das Gebietsschema En hinzu.  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7.  Kopieren Sie den Ordner C:\package, auf dem Visual Studio-Bootstrapper-Verzeichnis. Für Visual Studio 2010 ist dies das Verzeichnis der \Programme\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
## <a name="example"></a>Beispiel  
 Das Paketmanifest enthält gebietsschemaspezifischen Informationen, z. B. Fehlermeldungen, Software-Lizenzbedingungen, und Language Packs.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.txt">  
  
  <PackageFiles>  
    <PackageFile Name="eula.txt"/>  
  </PackageFiles>  
  
  <Strings>  
    <String Name="DisplayName">Custom Bootstrapper Package</String>  
    <String Name="Culture">en</String>  
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>  
    <String Name="GeneralFailure">A general error has occurred while   
installing this package.</String>  
  </Strings>  
</Package>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zum Produkt- und Paketschema](../deployment/product-and-package-schema-reference.md)