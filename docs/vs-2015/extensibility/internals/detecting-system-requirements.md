---
title: Erkennen von System Anforderungen | Microsoft-Dokumentation
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
ms.openlocfilehash: 467554b8e50878bcdf1029e4792bbf168a09fa11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840907"
---
# <a name="detecting-system-requirements"></a>Ermitteln von Systemanforderungen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein VSPackage ist nicht funktionsfähig, es sei denn, Visual Studio ist installiert. Wenn Sie Microsoft Windows Installer zum Verwalten der Installation des VSPackages verwenden, können Sie den Installer so konfigurieren, dass erkannt wird, ob Visual Studio installiert ist. Sie können es auch so konfigurieren, dass das System auf andere Anforderungen, z. b. eine bestimmte Version von Windows oder eine bestimmte Größe von RAM, überprüft wird.  
  
## <a name="detecting-visual-studio-editions"></a>Erkennen von Visual Studio-Editionen  
 Um zu ermitteln, ob eine Edition von Visual Studio installiert ist, vergewissern Sie sich, dass der Wert des Registrierungsschlüssels "Install" (REG_DWORD) 1 im entsprechenden Ordner lautet, wie in der folgenden Tabelle aufgeführt. Beachten Sie, dass es eine Hierarchie von Visual Studio-Editionen gibt:  
  
1. Enterprise  
  
2. Professionell  
  
3. Community  
  
   Wenn eine "höhere" Edition installiert ist, werden die Registrierungsschlüssel für diese Edition sowie für "niedrigere" Editionen hinzugefügt. Das heißt, wenn die Enterprise Edition installiert ist, wird der Installations Schlüssel auf 1 für Enterprise sowie für Professional-und Community-Editionen festgelegt. Daher müssen Sie nur die "höchste" Edition überprüfen, die Sie benötigen.  
  
> [!NOTE]
> In der 64-Bit-Version des Registrierungs-Editors werden unter HKEY_LOCAL_MACHINE \software\wow6432knoten 32-Bit-Schlüssel angezeigt \\ . Die Visual Studio-Schlüssel befinden sich unter HKEY_LOCAL_MACHINE \software\wow6432node\microsoft\devdiv\vs\wartung \\ .  
  
|Produkt|Schlüssel|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE \software\microsoft\devdiv\vs\servicing\14.0\enter Prise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE \software\microsoft\devdiv\vs\servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE \software\microsoft\devdiv\vs\servicing\14.0\community|  
|Visual Studio 2015 Shell (integriert und isoliert)|HKEY_LOCAL_MACHINE \software\microsoft\devdiv\vs\servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Erkennen, wenn Visual Studio ausgeführt wird  
 Das VSPackage kann nicht ordnungsgemäß registriert werden, wenn Visual Studio ausgeführt wird, wenn das VSPackage installiert ist. Der Installer muss erkennen, wenn Visual Studio ausgeführt wird, und dann die Installation des Programms ablehnen. Mit Windows Installer können Sie keine Tabelleneinträge verwenden, um eine solche Erkennung zu aktivieren. Stattdessen müssen Sie eine benutzerdefinierte Aktion wie folgt erstellen: Verwenden Sie die `EnumProcesses` Funktion, um den devenv.exe Prozess zu erkennen, und legen Sie dann entweder eine installereigenschaft fest, die in einer Startbedingung verwendet wird, oder bedingt ein Dialogfeld, in dem der Benutzer aufgefordert wird, Visual Studio zu schließen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
