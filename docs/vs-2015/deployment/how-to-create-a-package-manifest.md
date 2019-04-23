---
title: 'Vorgehensweise: Erstellen eines Paketmanifests | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c711c50ab484cc88b1d6aff5c8e3018cead69953
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60046014"
---
# <a name="how-to-create-a-package-manifest"></a>Vorgehensweise: Erstellen eines Paketmanifests
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um die Bereitstellung der erforderlichen Komponenten für Ihre Anwendung können Sie ein Bootstrapperpaket. Ein Bootstrapperpaket enthält eine einzelnes Produkt-Manifestdatei jedoch ein Paketmanifest für jedes Gebietsschema. Gemeinsam genutzte Funktionen in den verschiedenen lokalisierten Versionen sollten das Produktmanifest näher betrachten.  
  
 Weitere Informationen zu Paketmanifesten, finden Sie unter [Vorgehensweise: Erstellen eines Produktmanifests](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="creating-the-package-manifest"></a>Erstellen des Paketmanifests  
  
#### <a name="to-create-the-package-manifest"></a>Zum Erstellen des Paketmanifests  
  
1. Erstellen Sie ein Verzeichnis für die Bootstrapper-Paket. Dieses Beispiel verwendet die C:\package.  
  
2. Erstellen Sie ein Unterverzeichnis mit dem Namen des Gebietsschemas, beispielsweise "En" für Englisch aus.  
  
3. In Visual Studio, erstellen Sie eine XML-Datei mit dem Namen `package.xml`, und speichern Sie sie in den Ordner C:\package\en.  
  
4. Fügen Sie XML-Code, zum Auflisten der Name der Bootstrapper-Pakets, die Kultur für dieses lokalisierte Paketmanifest und die optionale Lizenzvertrag. Die folgende XML-Code verwendet die Variablen `DisplayName` und `Culture`, die in einem späteren Element definiert sind.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5. Fügen Sie XML-Code, um alle Dateien aufgelistet, die sich im Verzeichnis gebietsschemaspezifische befinden. Das folgende XML verwendet, eine Datei mit dem Namen eula.txt, die für gilt die **En** Gebietsschema.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6. Fügen Sie XML-Code, um lokalisierbare Zeichenfolgen für die Bootstrapper-Paket zu definieren. Das folgende XML fügt für das de-Gebietsschema-Zeichenfolgen.  
  
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
  
7. Kopieren Sie den C:\package-Ordner, in das Visual Studio-Bootstrapper-Verzeichnis. Für Visual Studio 2010 ist dies das Verzeichnis \Programme\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
## <a name="example"></a>Beispiel  
 Die Paketmanifest enthält gebietsschemaspezifischen Informationen, z. B. Fehlermeldungen, Software-Lizenzbedingungen, und Language Packs.  
  
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
