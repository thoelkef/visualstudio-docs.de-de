---
title: "Ermitteln von Systemanforderungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Setup, VSPackages"
  - "Startbedingungen"
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 50
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 50
---
# Ermitteln von Systemanforderungen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein VSPackage funktioniert nicht, wenn Visual Studio installiert ist. Wenn Sie Microsoft Windows Installer verwenden, um die Installation von Ihr VSPackage verwalten, können Sie das Installationsprogramm aus, um festzustellen, ob die Installation von Visual Studio konfigurieren. Sie können auch das System für andere Anforderungen, z. B. überprüfen, eine bestimmte Version von Windows oder einer bestimmten Menge an RAM konfigurieren.  
  
## Erkennen von Visual Studio\-Editionen  
 Um zu bestimmen, ob eine Edition von Visual Studio installiert ist, überprüfen Sie, dass der Wert des Registrierungsschlüssels installieren \(REG\_DWORD\) 1 in den entsprechenden Ordner, wie in der folgenden Tabelle aufgeführt. Beachten Sie, dass eine Hierarchie von Visual Studio\-Editionen:  
  
1.  Enterprise  
  
2.  Professionell  
  
3.  Community  
  
 Wenn eine "größer" Edition installiert ist, werden die Registrierungsschlüssel für diese Edition als auch für "kleiner" Editionen hinzugefügt. Wenn die Enterprise Edition installiert ist, ist der installieren\-Schlüssel, also 1 für Enterprise sowie Professional und Community Edition festgelegt. Daher müssen Sie nur für die Edition "höchste" überprüfen, die Sie benötigen.  
  
> [!NOTE]
>  In der 64\-Bit\-Version des Registrierungs\-Editor werden die 32\-Bit\-Schlüssel unter HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\ angezeigt. Die Visual Studio\-Schlüssel sind unter HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\DevDiv\\vs\\Servicing\\.  
  
|Produkt|Key|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\enterprise|  
|Visual Studio Professional 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\professional|  
|Visual Studio Community 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\community|  
|Visual Studio 2015 Shell \(integriert und isoliert\)|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell|  
  
## Erkennen, wenn Visual Studio ausgeführt wird  
 Das VSPackage werden nicht ordnungsgemäß registriert, wenn Visual Studio ausgeführt wird, wenn das VSPackage installiert ist. Das Installationsprogramm muss erkennen, wenn Visual Studio ausgeführt wird und dann zum Installieren des Programms ablehnen. Windows Installer können Sie die Einträge zu verwenden, um diese Erkennung aktivieren nicht. Stattdessen müssen erstellen Sie eine benutzerdefinierte Aktion, wie folgt: Verwenden der `EnumProcesses` Funktion zum Erkennen des devenv.exe\-Prozess, und legen Sie eine Installer\-Eigenschaft, die in einer Startbedingung oder bedingt verwendet wird, entweder Anzeigen eines Dialogfelds, das den Benutzer auffordert, Visual Studio zu schließen.  
  
## Siehe auch  
 [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)