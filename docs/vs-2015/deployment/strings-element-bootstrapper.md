---
title: '&lt;Strings- &gt; Element (Boots Trapper) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.NoStringsForCulture
- MSBuild.GenerateBootstrapper.ProductCultureNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Strings> element [bootstrapper]
ms.assetid: d5ea3613-5fc9-4a11-bef3-46a01178bf60
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dd799020e50121e2f3e9a6ba7ad90fd79a1241cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62421524"
---
# <a name="ltstringsgt-element-bootstrapper"></a>&lt;Strings- &gt; Element (Boots Trapper)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definiert lokalisierte Zeichen folgen für Produktnamen, Paketnamen und Installations Fehlermeldungen.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Strings>  
    <String  
        Name  
    >  
    </String>  
</Strings>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das- `Strings` Element ist ein untergeordnetes `Package` Element des-Elements. Sie besitzt keine Attribute.  
  
## <a name="string"></a>Zeichenfolge  
 Das- `String` Element ist ein untergeordnetes `Strings` Element des-Elements. Ein- `Strings` Element kann ein oder mehrere- `String` Elemente aufweisen.  
  
 `String` weist das folgende Attribut auf.  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`Name`|Erforderlich. Der Name der Zeichenfolge.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel werden alle englischen Zeichen folgen für das Installationsprogramm angegeben [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
```  
<Strings>  
    <String Name="DisplayName">.NET Framework 2.0</String>  
    <String Name="Culture">en</String>  
    <String Name="AdminRequired">Administrator permissions are required to install the .NET Framework 2.0. Contact your administrator.</String>  
    <String Name="InvalidPlatformWin9x">Installation of the .NET Framework 2.0 is not supported on Windows 95. Contact your application vendor.</String>  
    <String Name="InvalidPlatformWinNT">Installation of the .NET Framework 2.0 is not supported on Windows NT 4.0. Contact your application vendor.</String>  
    <String Name="InvalidPlatformIE">Installation of the .NET Framework 2.0 requires Internet Explorer 5.01 or greater. Contact your application vendor.</String>  
    <String Name="InvalidPlatformArchitecture">This version of the .NET Framework 2.0 is not supported on a 64-bit operating system. Contact your application vendor.</String>  
    <String Name="WindowsInstallerImproperInstall">Due to an error with Windows Installer, the installation of the .NET Framework 2.0 cannot proceed.</String>  
    <String Name="AnotherInstanceRunning">Another instance of setup is already running. The running instance must complete before this setup can proceed.</String>  
    <String Name="BetaNDPFailure">A beta version of the .NET Framework was detected on the computer. Uninstall any previous beta versions of .NET Framework before continuing.</String>  
    <String Name="GeneralFailure">A failure occurred attempting to install the .NET Framework 2.0.</String>  
    <String Name="DotNetFXExe">http://go.microsoft.com/fwlink/?LinkId=37283</String>  
    <String Name="InstMsiAExe">http://go.microsoft.com/fwlink/?LinkId=37285</String>  
    <String Name="Msi30Exe">http://go.microsoft.com/fwlink/?LinkId=37287</String>  
</Strings>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [\<Package>-Element](../deployment/package-element-bootstrapper.md)
