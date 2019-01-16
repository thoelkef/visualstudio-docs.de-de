---
title: 'Vorgehensweise: Erstellen eines Paketmanifests | Microsoft-Dokumentation'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1f965bdbd19193bfaa942d5f3635b0652f0e9c4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53943472"
---
# <a name="how-to-create-a-package-manifest"></a>Vorgehensweise: Erstellen eines Paketmanifests
Um die Bereitstellung der erforderlichen Komponenten für Ihre Anwendung können Sie ein Bootstrapperpaket. Ein Bootstrapperpaket enthält eine einzelnes Produkt-Manifestdatei jedoch ein Paketmanifest für jedes Gebietsschema. Gemeinsam genutzte Funktionen in den verschiedenen lokalisierten Versionen sollten das Produktmanifest näher betrachten.  
  
 Weitere Informationen zu Paketmanifesten, finden Sie unter [Vorgehensweise: Erstellen eines Produktmanifests](../deployment/how-to-create-a-product-manifest.md)  
  
## <a name="create-the-package-manifest"></a>Erstellen des Paketmanifests  
  
#### <a name="to-create-the-package-manifest"></a>Zum Erstellen des Paketmanifests  
  
1.  Erstellen Sie ein Verzeichnis für die Bootstrapper-Paket. Dieses Beispiel verwendet *C:\package*.  
  
2.  Erstellen Sie ein Unterverzeichnis mit dem Namen des Gebietsschemas, z. B. *En* für Englisch.  
  
3.  In Visual Studio, erstellen Sie eine XML-Datei mit dem Namen *"Package.xml"*, und speichern sie die *C:\package\en* Ordner.  
  
4.  Fügen Sie XML-Code, zum Auflisten der Name der Bootstrapper-Pakets, die Kultur für dieses lokalisierte Paketmanifest und die optionale Lizenzvertrag. Die folgende XML-Code verwendet die Variablen `DisplayName` und `Culture`, die in einem späteren Element definiert sind.  
  
    ```xml  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Fügen Sie XML-Code, um alle Dateien aufgelistet, die sich im Verzeichnis gebietsschemaspezifische befinden. Die folgende XML-Code verwendet eine Datei mit dem Namen *eula.txt* , die gilt für die **En** Gebietsschema.  
  
    ```xml  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Fügen Sie XML-Code, um lokalisierbare Zeichenfolgen für die Bootstrapper-Paket zu definieren. Das folgende XML fügt Fehlerzeichenfolgen für die **En** Gebietsschema.  
  
    ```xml  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7.  Kopieren der *C:\package* Ordner auf dem Visual Studio-Bootstrapper-Verzeichnis. Für Visual Studio 2010 ist dies die *\Programme\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* Verzeichnis.  
  
## <a name="example"></a>Beispiel  
 Die Paketmanifest enthält gebietsschemaspezifischen Informationen, z. B. Fehlermeldungen, Software-Lizenzbedingungen, und Language Packs.  
  
```xml  
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