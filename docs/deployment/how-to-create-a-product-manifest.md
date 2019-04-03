---
title: 'Vorgehensweise: Erstellen eines Produktmanifests | Microsoft-Dokumentation'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48bed4a357809a672b1fc80063ca6743670cbb42
ms.sourcegitcommit: da73f7a0cf1795d5d400c0897ae3326191435dd0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2019
ms.locfileid: "58568100"
---
# <a name="how-to-create-a-product-manifest"></a>Vorgehensweise: Erstellen eines Produktmanifests
Um die erforderlichen Komponenten für Ihre Anwendung bereitstellen möchten, können Sie ein Bootstrapperpaket erstellen. Ein Bootstrapperpaket enthält eine einzelnes Produkt-Manifestdatei jedoch ein Paketmanifest für jedes Gebietsschema. Die Paketmanifest enthält Lokalisierung-spezifische Aspekte des Pakets. Dies schließt die Zeichenfolgen, durch den Endbenutzer-Lizenzverträge und die Language Packs.

 Weitere Informationen zu Paketmanifesten, finden Sie unter [Vorgehensweise: Erstellen eines Paketmanifests](../deployment/how-to-create-a-package-manifest.md).

## <a name="create-the-product-manifest"></a>Das Produktmanifest erstellen

#### <a name="to-create-the-product-manifest"></a>Das Produktmanifest erstellen

1.  Erstellen Sie ein Verzeichnis für die Bootstrapper-Paket. Dieses Beispiel verwendet die C:\package.

2.  Erstellen Sie in Visual Studio eine neue XML-Datei namens *product.xml*, und speichern sie die *C:\package* Ordner.

3.  Fügen Sie den folgenden XML-Code, um den XML-Namespace und Produkt-Code für das Paket beschreiben. Ersetzen Sie den Produktcode mit einem eindeutigen Bezeichner für das Paket an.

    ```xml
    <Product
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
    ProductCode="Custom.Bootstrapper.Package">
    ```

4.  Fügen Sie XML-Code, um anzugeben, dass das Paket abhängig ist. Dieses Beispiel verwendet eine Abhängigkeit auf Microsoft Windows Installer 3.1 oder höher.

    ```xml
    <RelatedProducts>
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
      </RelatedProducts>
    ```

5.  Fügen Sie XML-Code, um alle Dateien aufgelistet, die in das Bootstrapperpaket zu sind. In diesem Beispiel verwendet den Namen der Paketdatei *"CorePackage.msi"*.

    ```xml
    <PackageFiles>
        <PackageFile Name="CorePackage.msi"/>
    </PackageFiles>
    ```

6.  Kopieren oder verschieben Sie die *"CorePackage.msi"* -Datei in die *C:\package* Ordner.

7.  Fügen Sie XML-Code, zum Installieren des Pakets mithilfe von Bootstrapperbefehlen. Der Bootstrapper fügt automatisch die **/qn /** flag, das die *MSI* -Datei, die im Hintergrund installiert wird. Wenn die Datei ist eine *.exe*, führt der Bootstrapper die *.exe* -Datei mit der Shell. Das folgende XML zeigt keine Argumente *"CorePackage.msi"*, Sie können jedoch Befehlszeilenargument in der `Arguments` Attribut.

    ```xml
    <Commands>
        <Command PackageFile="CorePackage.msi" Arguments="">
    ```

8.  Fügen Sie den folgenden XML-Code, um festzustellen, ob dieser Bootstrapper-Paket installiert ist. Ersetzen Sie den Produktcode, durch die GUID für die redistributable-Komponente.

    ```xml
    <InstallChecks>
        <MsiProductCheck
            Property="IsMsiInstalled"
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
    </InstallChecks>
    ```

9. Fügen Sie XML-Code, um das Bootstrapperverhalten abhängig zu ändern, wenn der Bootstrapper Komponenten bereits installiert ist. Wenn die Komponente installiert ist, wird der Bootstrapper-Paket nicht ausgeführt. Das folgende XML wird überprüft, ob der aktuelle Benutzer ein Administrator ist, da diese Komponente Administratorrechte erforderlich sind.

    ```xml
    <InstallConditions>
        <BypassIf
           Property="IsMsiInstalled"
           Compare="ValueGreaterThan" Value="0"/>
        <FailIf Property="AdminUser"
            Compare="ValueNotEqualTo" Value="True"
            String="NotAnAdmin"/>
    </InstallConditions>
    ```

10. Fügen Sie XML-Code, um Exitcodes festzulegen, wenn die Installation erfolgreich ist, und wenn ein Neustart erforderlich ist. Das folgende XML zeigt, dass die schlägt fehl und FailReboot Exitcodes angegeben, dass der Bootstrapper Installieren von Paketen nicht fortgesetzt wird.

    ```xml
    <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
    </ExitCodes>
    ```

11. Fügen Sie das folgende XML, wenn Sie im Abschnitt für die Bootstrapperbefehle zu beenden.

    ```xml
        </Command>
    </Commands>
    ```

12. Verschieben der *C:\package* Ordner auf dem Visual Studio-Bootstrapper-Verzeichnis. Für Visual Studio 2010 ist dies die *\Programme\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* Verzeichnis.

## <a name="example"></a>Beispiel
 Das Produktmanifest enthält installationsanweisungen für benutzerdefinierte erforderliche Komponenten.

```xml
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
- [Referenz zum Produkt- und Paketschema](../deployment/product-and-package-schema-reference.md)