---
title: "Gewusst wie: Erstellen eines Produktmanifests | Microsoft Docs"
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
  - "Abhängigkeiten, Benutzerdefiniertes Bootstrapperpaket"
  - "Voraussetzungen, Benutzerdefiniertes Bootstrapperpaket"
  - "Produktdateien [ClickOnce]"
  - "Produktdateien [Windows Installer]"
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Gewusst wie: Erstellen eines Produktmanifests
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Zur Bereitstellung der erforderlichen Komponenten für die Anwendung können Sie ein Bootstrapperpaket erstellen.  Ein Bootstrapperpaket enthält eine einzelne Produktmanifestdatei, aber ein Paketmanifest für jedes Gebietsschema.  Das Paketmanifest enthält lokalisierungsspezifische Aspekte des Pakets.  Dies schließt Zeichenfolgen, Software\-Lizenzbedingungen und die Language Packs ein.  
  
 Weitere Informationen zu Produktmanifesten finden Sie unter [Gewusst wie: Erstellen eines Paketmanifests](../deployment/how-to-create-a-package-manifest.md).  
  
## Erstellen des Produktmanifests  
  
#### So erstellen Sie das Produktmanifest  
  
1.  Erstellen Sie ein Verzeichnis für das Bootstrapperpaket.  In diesem Beispiel wird der Pfad "C:\\package" verwendet.  
  
2.  Erstellen Sie in Visual Studio eine XML\-Datei mit dem Namen `product.xml`, und speichern Sie sie im Ordner "C:\\package".  
  
3.  Fügen Sie das folgende XML\-Element hinzu, um den XML\-Namespace und den Produktcode für das Paket zu beschreiben.  Ersetzen Sie den Produktcode durch einen eindeutigen Bezeichner für das Paket.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  Fügen Sie ein XML\-Element hinzu, um anzugeben, dass das Paket eine Abhängigkeit besitzt.  In diesem Beispiel wird eine Abhängigkeit von Microsoft Windows Installer 3.1 verwendet.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  Fügen Sie ein XML\-Element hinzu, um alle Dateien aufzuführen, die im Bootstrapperpaket enthalten sind.  In diesem Beispiel wird für die Paketdatei der Name "CorePackage.msi" verwendet.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  Kopieren oder verschieben Sie die Datei "CorePackage.msi" in den Ordner "C:\\package".  
  
7.  Fügen Sie ein XML\-Element hinzu, um das Paket mithilfe von Bootstrapperbefehlen zu installieren.  Der Bootstrapper fügt der MSI\-Datei automatisch das **\/qn**\-Kennzeichen hinzu, die automatisch installiert wird.  Handelt es sich um eine EXE\-Datei, wird vom Bootstrapper die EXE\-Datei mithilfe der Shell ausgeführt.  Das folgende XML\-Element zeigt keine Argumente für "CorePackage.msi". Sie können aber ein Befehlszeilenargument in das Attribut für Argumente ablegen.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  Fügen Sie das folgende XML\-Element hinzu, um zu prüfen, ob dieses Bootstrapperpaket installiert ist.  Ersetzen Sie den Produktcode durch die GUID für die weitervertreibbare Komponente.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Fügen Sie ein XML\-Element hinzu, um das Bootstrapperverhalten in Abhängigkeit vom Installationsstatus der Bootstrapperkomponente \(bereits installiert, nicht installiert\) zu ändern.  Ist die Komponente installiert, wird das Bootstrapperpaket nicht ausgeführt.  Mit dem folgenden XML\-Element wird überprüft, ob der aktuelle Benutzer Administrator ist, da diese Komponente Administratorrechte erfordert.  
  
    ```  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. Fügen Sie ein XML\-Element hinzu, um Exitcodes festzulegen, wenn die Installation erfolgreich war und ein Neustart erforderlich ist.  Mit dem folgenden XML\-Element werden die Fehler\- und FailReboot\-Exitcodes veranschaulicht, durch die angegeben wird, dass der Bootstrapper keine weiteren Pakete installiert.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Fügen Sie das folgende XML\-Element hinzu, um den Abschnitt für Bootstrapperbefehle zu beenden.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Verschieben Sie den Ordner "C:\\package" in das Bootstrapperverzeichnis von Visual Studio.  In Visual Studio 2010 ist dies das Verzeichnis "\\Programme\\Microsoft SDKs\\Windows\\v7 .0A \\Bootstrapper\\Packages".  
  
## Beispiel  
 Das Produktmanifest enthält Installationsanweisungen für benutzerdefinierte erforderliche Komponenten.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Custom.Bootstrapper.Package">  
  
  <RelatedProducts>  
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
  </RelatedProducts>  
  
  <PackageFiles>  
    <PackageFile Name="CorePackage.msi"/>  
  </PackageFiles>  
  
  <InstallChecks>  
    <MsiProductCheck Product="IsMsiInstalled"   
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
  </InstallChecks>  
  
  <Commands>  
    <Command PackageFile="CorePackage.msi" Arguments="">  
  
      <InstallConditions>  
        <BypassIf Property="IsMsiInstalled"  
          Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
          Compare="ValueNotEqualTo" Value="True"  
         String="NotAnAdmin"/>  
      </InstallConditions>  
  
      <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
      </ExitCodes>  
    </Command>  
  </Commands>  
</Product>  
```  
  
## Siehe auch  
 [Referenz zum Produkt\- und Paketschema](../deployment/product-and-package-schema-reference.md)