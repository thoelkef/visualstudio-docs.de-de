---
title: Ersetzen von Zeichenfolgen verwendet. PKGDEF und. Pkgundef-Dateien | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0405e18419baf8bc152331a2bcfc7254ec602d1b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Ersetzen von Zeichenfolgen verwendet. PKGDEF und. Pkgundef-Dateien
Können Sie die unten aufgeführten, in der PKGDEF Ersatzzeichenfolgen und -isolierten shellanwendung .pkgundef-Dateien, die Sie für Ihre Visual Studio definieren.  
  
## <a name="substitution-strings"></a>Ersetzen von Zeichenfolgen  
  
|Zeichenfolge|Beschreibung|  
|------------|-----------------|  
|$=*RegistryEntry*$|Der Wert, der die *RegistryEntry* Eintrag. Wenn die Registrierungszeichenfolge Eintrag in einem umgekehrten Schrägstrich enden (\\), und klicken Sie dann den Standardwert des Registrierungsunterschlüssels verwendet wird. Beispielsweise die Ersetzung $ string = HKEY_CURRENT_USER\Environment\TEMP$ wird auf den temporären Ordners des aktuellen Benutzers erweitert.|  
|$AppName$|Der qualifizierte Name der Anwendung, die an die Einstiegspunkte AppEnv.dll übergeben wird. Der qualifizierte Name besteht aus den Namen der Anwendung, einem Unterstrich und der Klassenbezeichner (CLSID) der Anwendung-Automatisierungsobjekts, der auch als der Wert der Einstellung in der PKGDEF-Datei des Projekts ThisVersionDTECLSID aufgezeichnet wird.|  
|$AppDataLocalFolder|Der Unterordner %LocalAppData% für diese Anwendung.|  
|$BaseInstallDir$|Der vollständige Pfad des Speicherorts, in dem Visual Studio installiert wurde.|  
|$CommonFiles$|Der Wert der Variable %CommonProgramFiles% in Umgebung.|  
|$MyDocuments$|Der vollständige Pfad der Ordner "Eigene Dokumente" des aktuellen Benutzers.|  
|$PackageFolder$|Der vollständige Pfad des Verzeichnisses, das die Paketdateien für die Assembly für die Anwendung enthält.|  
|$ProgramFiles$|Der Wert des % ProgramFiles% %-Umgebungsvariable.|  
|$RootFolder$|Der vollständige Pfad des Stammverzeichnisses der Anwendung.|  
|$RootKey$|Der Stamm-Registrierungsschlüssel für die Anwendung. Standardmäßig ist der Stamm im HKEY_CURRENT_USER\Software\\*CompanyName*\\*Projektname*\\*VersionNumber* (Wenn die Anwendung ausgeführt wird, _Config wird mit diesem Schlüssel angefügt). Es wird festgelegt, durch den RegistryRoot-Wert in der *SolutionName*PKGDEF-Datei.<br /><br /> Die $RootKey$ Zeichenfolge kann verwendet werden, um einen Registrierungswert unter dem Anwendungsunterschlüssel abzurufen. Z. B. die Zeichenfolge "$= $RootKey$ \AppIcon$" gibt den Wert des Eintrags AppIcon Unterschlüssel Stamm Anwendung zurück.<br /><br /> Der Parser die PKGDEF-Datei sequenziell verarbeitet, und kann einen Registrierungseintrag unter dem Anwendungsunterschlüssel nur zugreifen, wenn der Eintrag zuvor definiert wurde|  
|$ShellFolder$|Der vollständige Pfad des Speicherorts, in dem Visual Studio installiert wurde.|  
|$System$|Der Ordner "Windows\System32".|  
|$WINDIR$|Der Ordner "Windows".|  
  
 Wenn der Parser nicht der Ersatzzeichenfolge erkennt oder keine genaue der den Wert eines Registrierungseintrags oder eine Umgebungsvariable Bestimmung, führt es nicht Ersetzung auf diesen Teil der Zeichenfolge aus.