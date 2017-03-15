---
title: Ersetzen von Zeichenfolgen verwendet. PKGDEF und. Pkgundef Dateien | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: c64a760b821663ba488f6f9dab415bad13d6047d
ms.lasthandoff: 02/22/2017

---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Ersetzen von Zeichenfolgen verwendet. PKGDEF und. Pkgundef-Dateien
Können Sie in der PKGDEF aufgeführten Ersatzzeichenfolgen und .pkgundef-Dateien, die Sie für Ihre Visual Studio definieren isolierte Shell-Anwendung.  
  
## <a name="substitution-strings"></a>Ersetzen von Zeichenfolgen  
  
|Zeichenfolge|Beschreibung|  
|------------|-----------------|  
|$=*RegistryEntry*$|Der Wert der *RegistryEntry* Eintrag. Wenn die Zeichenfolge für die Registrierung einen umgekehrten Schrägstrich endet (\\), wird der Standardwert des Registrierungsunterschlüssels verwendet. Z. B. die Ersetzung string $= HKEY_CURRENT_USER\Environment\TEMP$ des temporären Ordners des aktuellen Benutzers erweitert.|  
|$AppName$|Der qualifizierte Name der Anwendung, die an die Einstiegspunkte AppEnv.dll übergeben wird. Der qualifizierte Name besteht aus den Namen der Anwendung, einem Unterstrich und den Klassenbezeichner (CLSID) des Automatisierungsobjekts Anwendung, die auch als Wert für die ThisVersionDTECLSID-Einstellung in der PKGDEF-Datei des Projekts erfasst wird.|  
|$AppDataLocalFolder|Der Unterordner unter % LocalAppData% für diese Anwendung.|  
|$BaseInstallDir$|Der vollständige Pfad des Speicherorts, auf dem Visual Studio installiert wurde.|  
|$CommonFiles$|Der Wert der Variable %CommonProgramFiles% Umgebung.|  
|$MyDocuments$|Der vollständige Pfad des Ordners "Eigene Dateien" des aktuellen Benutzers.|  
|$PackageFolder$|Der vollständige Pfad des Verzeichnisses, das die Paketdateien für die Assembly für die Anwendung enthält.|  
|$ProgramFiles$|Der Wert des % ProgramFiles %-Umgebungsvariable.|  
|$RootFolder$|Der vollständige Pfad des Stammverzeichnisses der Anwendung.|  
|$RootKey$|Der Stamm-Registrierungsschlüssel für die Anwendung. Standardmäßig ist das Stammverzeichnis in HKEY_CURRENT_USER\Software\\*CompanyName*\\*Projektname*\\*VersionNumber* (wenn die Anwendung ausgeführt wird, _Config wird angefügt, diesem Schlüssel). Es wird festgelegt, durch den RegistryRoot-Wert in der *SolutionName*PKGDEF-Datei.<br /><br /> Die $RootKey$ Zeichenfolge kann verwendet werden, um einen Registrierungswert unter dem Anwendungsunterschlüssel abzurufen. Z. B. die Zeichenfolge "$= $RootKey$ \AppIcon$" den Wert des Eintrags AppIcon Unterschlüssel Stamm Anwendung zurück.<br /><br /> Der Parser die PKGDEF-Datei sequenziell verarbeitet und kann einen Registrierungseintrag unter dem Anwendungsunterschlüssel nur zugreifen, wenn der Eintrag zuvor definiert wurde|  
|$ShellFolder$|Der vollständige Pfad des Speicherorts, auf dem Visual Studio installiert wurde.|  
|$System$|Der Ordner "Windows\System32".|  
|$WINDIR$|Der Windows-Ordner.|  
  
 Wenn der Parser die Ersatzzeichenfolge nicht erkannt, oder es kann nicht den Wert eines Registrierungseintrags oder eine Umgebungsvariable bestimmen, und klicken Sie dann auf diesen Teil der Zeichenfolge keine Ersetzung ausgeführt wird.
