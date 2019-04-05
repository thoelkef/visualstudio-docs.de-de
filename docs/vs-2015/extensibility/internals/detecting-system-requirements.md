---
title: Ermitteln von Systemanforderungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 51
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cdc69441de852e16adc047465aeec30003fe5170
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961603"
---
# <a name="detecting-system-requirements"></a>Ermitteln von Systemanforderungen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Eine VSPackage funktioniert nicht, es sei denn, die Visual Studio installiert ist. Wenn Sie Microsoft Windows Installer, zum Verwalten der Installation von einem VSPackage verwenden, können Sie das Installationsprogramm aus, um festzustellen, ob die Installation von Visual Studio konfigurieren. Sie können auch damit das System für andere Anforderungen, z. B. überprüfen, eine bestimmte Version von Windows oder einer bestimmten Menge an RAM konfigurieren.  
  
## <a name="detecting-visual-studio-editions"></a>Erkennen von Visual Studio-Editionen  
 Um zu bestimmen, ob eine Edition von Visual Studio installiert ist, überprüfen Sie, dass der Wert des Registrierungsschlüssels installieren (REG_DWORD) 1 in den entsprechenden Ordner, in der folgenden Tabelle aufgeführt. Beachten Sie, dass eine Hierarchie von Visual Studio-Editionen:  
  
1. Enterprise  
  
2. Professionell  
  
3. Community  
  
   Wenn eine "höhere" Edition installiert ist, werden die Registrierungsschlüssel für diese Edition als auch für "kleiner" Editionen hinzugefügt. Wenn es sich bei die Enterprise Edition installiert ist, wird der Schlüssel für die Installation, also 1 für Enterprise sowie Professional und Community-Editionen festgelegt. Aus diesem Grund müssen Sie nur für die Edition "höchsten" zu überprüfen, die Sie benötigen.  
  
> [!NOTE]
>  32-Bit-Schlüssel werden in der 64-Bit-Version des Registrierungs-Editor unter HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node angezeigt\\. Die Visual Studio-Schlüssel befinden sich unter HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\.  
  
|Produkt|Key|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (integriert und isoliert)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Erkennen, wenn Visual Studio ausgeführt wird  
 Das VSPackage kann nicht ordnungsgemäß registriert werden, wenn Visual Studio ausgeführt wird, wenn VSPackages installiert ist. Das Installationsprogramm muss erkennen, wenn Visual Studio ausgeführt wird, und klicken Sie dann zum Installieren des Programms verweigert. Windows Installer können nicht Sie Einträge zu verwenden, um diese Erkennung zu aktivieren. Stattdessen müssen Sie eine benutzerdefinierte Aktion, wie folgt erstellen: Verwenden der `EnumProcesses` -Funktion zum Erkennen des devenv.exe-Prozess, und legen Sie dann entweder eine Installer-Eigenschaft, die in eine Startbedingung oder bedingt verwendet wird, zeigt ein Dialogfeld, das den Benutzer auffordert, Visual Studio zu schließen.  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
