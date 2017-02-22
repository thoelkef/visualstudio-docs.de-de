---
title: "Gewusst wie: Erstellen eines Paketmanifests | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Abhängigkeiten, Benutzerdefinierte Bootstrapperpakete"
  - "Paketdateien [ClickOnce]"
  - "Paketdateien [Windows Installer]"
  - "Voraussetzungen, Benutzerdefiniertes Bootstrapperpaket"
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Gewusst wie: Erstellen eines Paketmanifests
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Zur Bereitstellung der erforderlichen Komponenten für die Anwendung können Sie ein Bootstrapperpaket verwenden.  Ein Bootstrapperpaket enthält eine einzelne Produktmanifestdatei, aber ein Paketmanifest für jedes Gebietsschema.  Die Funktionalität zwischen verschiedenen lokalisierten Versionen sollte in das Produktmanifest einfließen.  
  
 Weitere Informationen zu Paketmanifesten finden Sie unter [Gewusst wie: Erstellen eines Produktmanifests](../deployment/how-to-create-a-product-manifest.md).  
  
## Erstellen des Paketmanifests  
  
#### So erstellen Sie das Paketmanifest  
  
1.  Erstellen Sie ein Verzeichnis für das Bootstrapperpaket.  In diesem Beispiel wird der Pfad "C:\\package" verwendet.  
  
2.  Erstellen Sie ein Unterverzeichnis mit dem Namen des Gebietsschemas, z. B. "en" für Englisch.  
  
3.  Erstellen Sie in Visual Studio eine XML\-Datei, nennen Sie sie `package.xml`, und speichern Sie sie im Ordner "C:\\package\\en".  
  
4.  Fügen Sie ein XML\-Element hinzu, um den Namen des Bootstrapperpakets, die Kultur für dieses lokalisierte Paketmanifest und den optionalen Lizenzvertrag aufzuführen.  Das folgende XML\-Element verwendet die Variablen `DisplayName` und `Culture`, die in einem späteren Element definiert werden.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Fügen Sie ein XML\-Element hinzu, um alle Dateien aufzuführen, die im gebietsschemaspezifischen Verzeichnis enthalten sind.  Das folgende XML\-Element verwendet die Datei "eula.txt", die für das Gebietsschema **en** anwendbar ist.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Fügen Sie ein XML\-Element hinzu, um lokalisierbare Zeichenfolgen für das Bootstrapperpaket zu definieren.  Das folgende XML\-Element fügt Fehlerzeichenfolgen für das Gebietsschema "en" hinzu.  
  
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
  
7.  Kopieren Sie den Ordner "C:\\package" in das Bootstrapperverzeichnis von Visual Studio.  In Visual Studio 2010 ist dies das Verzeichnis "\\Programme\\Microsoft SDKs\\Windows\\v7 .0A \\Bootstrapper\\Packages".  
  
## Beispiel  
 Das Paketmanifest enthält gebietsschemaspezifische Informationen, z. B. Fehlermeldungen, Softwarelizenzbedingungen und Language Packs.  
  
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
  
## Siehe auch  
 [Referenz zum Produkt\- und Paketschema](../deployment/product-and-package-schema-reference.md)