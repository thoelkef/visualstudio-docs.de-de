---
title: 'Vorgehensweise: Erstellen eines Produktmanifests | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 116a54bae39738f95503ae9ca6e6cbac45c2db47
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-product-manifest"></a>Gewusst wie: Erstellen eines Produktmanifests
Um die erforderlichen Komponenten für Ihre Anwendung bereitstellen, können Sie ein Bootstrapperpaket erstellen. Ein Bootstrapperpaket enthält eine einzelne Produktmanifestdatei aber ein Paketmanifest für jedes Gebietsschema. Das Paketmanifest enthält Lokalisierung-spezifische Aspekte des Pakets. Dies schließt die Zeichenfolgen, die Endbenutzer-Lizenzverträge und die Language Packs.  
  
 Weitere Informationen zu Produktmanifesten finden Sie unter [Vorgehensweise: Erstellen eines Paketmanifests](../deployment/how-to-create-a-package-manifest.md).  
  
## <a name="creating-the-product-manifest"></a>Das Produktmanifest erstellen  
  
#### <a name="to-create-the-product-manifest"></a>Das Produktmanifest erstellen  
  
1.  Erstellen Sie ein Verzeichnis für das Bootstrapperpaket. Dieses Beispiel verwendet die C:\package.  
  
2.  In Visual Studio, erstellen Sie eine neue XML-Datei namens `product.xml`, und speichern sie den Ordner "C:\package".  
  
3.  Fügen Sie die folgenden XML-Code, um den XML-Namespace und Produkt-Code für das Paket beschreiben. Ersetzen Sie den Produktcode durch einen eindeutigen Bezeichner für das Paket an.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  Fügen Sie XML-Code, um anzugeben, dass das Paket eine Abhängigkeit aufweist. Dieses Beispiel verwendet eine Abhängigkeit auf Microsoft Windows Installer 3.1 oder höher.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  Fügen Sie XML-Code, um alle Dateien aufgelistet, die in die Bootstrapper-Pakets sind. Dieses Beispiel verwendet den Namen der Paketdatei "CorePackage.msi".  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  Kopieren Sie oder verschieben Sie die Datei "CorePackage.msi" in den Ordner C:\package.  
  
7.  Fügen Sie XML-Code, zum Installieren des Pakets mithilfe von Bootstrapperbefehlen. Der Bootstrapper fügt automatisch die **/qn /** Flag in der MSI-Datei, die automatisch installiert wird. Wenn die Datei eine .exe ist, wird der Bootstrapper die .exe-Datei über die Befehlsshell ausgeführt. Das folgende XML zeigt keine Argumente für "CorePackage.msi", aber die "Arguments"-Attributs Befehlszeilenargument abgelegt.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  Fügen Sie die folgenden XML-Code, um festzustellen, ob diese Bootstrapper-Pakets installiert ist. Ersetzen Sie den Produktcode durch die GUID für die weitervertreibbare Komponente.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Fügen Sie XML-Code, um das Bootstrapperverhalten abhängig zu ändern, wenn die Bootstrapperkomponente bereits installiert ist. Wenn die Komponente installiert ist, wird das Bootstrapperpaket nicht ausgeführt. Das folgende XML wird überprüft, ob der aktuelle Benutzer ein Administrator ist, da diese Komponente sind Administratorrechte erforderlich.  
  
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
  
10. Fügen Sie XML-Code, um Exitcodes festzulegen, wenn die Installation erfolgreich ist und ob ein Neustart erforderlich ist. Das folgende XML zeigt, dass die schlägt fehl und FailReboot Exitcodes an, dass der Bootstrapper Installieren von Paketen nicht fortgesetzt werden.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Fügen Sie das folgende XML, um den Abschnitt für die Bootstrapperbefehle zu beenden.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Verschieben Sie den Ordner C:\package, auf dem Visual Studio-Bootstrapper-Verzeichnis. Für Visual Studio 2010 ist dies das Verzeichnis der \Programme\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
## <a name="example"></a>Beispiel  
 Das Produktmanifest enthält installationsanweisungen für benutzerdefinierte erforderliche Komponenten.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zum Produkt- und Paketschema](../deployment/product-and-package-schema-reference.md)