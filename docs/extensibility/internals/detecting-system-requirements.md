---
title: Ermitteln von Systemanforderungen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5e98235bd224876b00714e1f71210ea69cb6faff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="detecting-system-requirements"></a>Ermitteln von Systemanforderungen
Eine VSPackage kann nicht ausgeführt werden, es sei denn, die Visual Studio installiert ist. Wenn Sie Microsoft Windows Installer verwenden, um die Installation von Ihr VSPackage zu verwalten, können Sie das Installationsprogramm aus, um festzustellen, ob die Installation von Visual Studio konfigurieren. Sie können auch auf das System für andere Anforderungen, z. B. Überprüfen einer bestimmten Version von Windows oder eine bestimmte Menge an RAM konfigurieren.  
  
## <a name="detecting-visual-studio-editions"></a>Erkennen von Visual Studio-Editionen  
 Um zu bestimmen, ob eine Edition von Visual Studio installiert ist, überprüfen Sie, dass der Wert des Registrierungsschlüssels installieren (REG_DWORD) 1 in den entsprechenden Ordner, wie in der folgenden Tabelle aufgeführt. Beachten Sie, dass eine Hierarchie von Visual Studio-Editionen:  
  
1.  Enterprise  
  
2.  Professionell  
  
3.  Community  
  
 Wenn eine "größer" Edition installiert ist, werden die Registrierungsschlüssel für diese Edition als auch für "kleiner" Editionen hinzugefügt. Wenn die Enterprise Edition installiert ist, wird der Schlüssel für die Installation, also auf 1 für Enterprise sowie für die Editionen Professional und Community festgelegt. Aus diesem Grund sollten Sie nur für die Edition "höchsten" zu überprüfen, die Sie benötigen.  
  
> [!NOTE]
>  In der 64-Bit-Version des Registrierungs-Editor-32-Bit-Schlüssel werden angezeigt, unter HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\. Die Visual Studio-Schlüssel befinden sich unter HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\.  
  
|Produkt|Key|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (integriert und isoliert)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Wenn Visual Studio ausgeführt wird  
 Das VSPackage werden nicht ordnungsgemäß registriert, wenn Visual Studio ausgeführt wird, wenn das VSPackage installiert ist. Das Installationsprogramm muss erkennen, wenn Visual Studio ausgeführt wird und klicken Sie dann zum Installieren des Programms ablehnen. Windows Installer können nicht Sie Tabelleneinträge zu verwenden, um diese Erkennung aktivieren. Sie müssen stattdessen erstellen eine benutzerdefinierte Aktion wie folgt: Verwenden der `EnumProcesses` Funktion, um den Prozess devenv.exe erkennen, und legen Sie eine Installer-Eigenschaft, die in einer Startbedingung oder bedingt verwendet wird, entweder angezeigt, die den Benutzer auffordert, schließen Sie das Dialogfeld Visual Studio.  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)