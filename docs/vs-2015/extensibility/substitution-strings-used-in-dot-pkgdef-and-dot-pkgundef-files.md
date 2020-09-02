---
title: In verwendete Ersetzungs Zeichenfolgen. Pkgdef und. Pkgundef-Dateien | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 47434d9d1dfcedeeaea330b1d65645d7a632c6e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160537"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>In PKGDEF- und PKGUNDEF-Dateien verwendete Ersetzungszeichenfolgen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die unten aufgeführten Ersatz Zeichenfolgen in den pkgdef-und pkgundef-Dateien verwenden, die Sie für Ihre Visual Studio-Anwendung für isolierte Shell definieren.  
  
## <a name="substitution-strings"></a>Ersatz Zeichenfolgen  
  
|Zeichenfolge|Beschreibung|  
|------------|-----------------|  
|$=*RegistryEntry*$|Der Wert des *RegistryEntry* -Eintrags. Wenn die Registrierungs Eintrags Zeichenfolge mit einem umgekehrten Schrägstrich ( \\ ) endet, wird der Standardwert des Registrierungs unter Schlüssels verwendet. Beispielsweise wird die Ersetzungs Zeichenfolge $ = HKEY_CURRENT_USER \umgebungs\temp $ auf den temporären Ordner des aktuellen Benutzers erweitert.|  
|$AppName $|Der qualifizierte Name der Anwendung, die an die AppEnv.dll Einstiegspunkte übermittelt wird. Der qualifizierte Name besteht aus dem Anwendungsnamen, einem Unterstrich und dem Klassen Bezeichner (CLSID) des Application Automation-Objekts, das auch als Wert der thisversiondteclsid-Einstellung in der Project. pkgdef-Datei aufgezeichnet wird.|  
|$AppDataLocalFolder|Der Unterordner unter "% LocalAppData%" für diese Anwendung.|  
|$BaseInstallDir $|Der vollständige Pfad des Speicher Orts, an dem Visual Studio installiert wurde.|  
|$CommonFiles $|Der Wert der Umgebungsvariablen% COMMONPROGRAMFILES%.|  
|$MyDocuments $|Der vollständige Pfad des Ordners "eigene Dateien" des aktuellen Benutzers.|  
|$PackageFolder $|Der vollständige Pfad des Verzeichnisses, das die paketassemblydateien für die Anwendung enthält.|  
|$ProgramFiles $|Der Wert der Umgebungsvariablen% Program Files%.|  
|$RootFolder $|Der vollständige Pfad des Stamm Verzeichnisses der Anwendung.|  
|$RootKey $|Der Stamm Registrierungsschlüssel für die Anwendung. Standardmäßig befindet sich der Stamm in HKEY_CURRENT_USER \Software \\ *CompanyName* \\ *ProjectName* \\ *VersionNumber* (wenn die Anwendung ausgeführt wird, wird _Config an diesen Schlüssel angehängt). Sie wird durch den RegistryRoot-Wert in der Datei " *SolutionName*. pkgdef" festgelegt.<br /><br /> Der $RootKey $ String kann verwendet werden, um einen Registrierungs Wert unter dem Anwendungs Unterschlüssel abzurufen. Beispielsweise gibt die Zeichenfolge "$ = $RootKey $ \appicon $" den Wert des AppIcon-Eintrags unter dem Stamm Unterschlüssel der Anwendung zurück.<br /><br /> Der Parser verarbeitet die pkgdef-Datei sequenziell und kann nur auf einen Registrierungs Eintrag unter dem Anwendungs Unterschlüssel zugreifen, wenn der Eintrag zuvor definiert wurde.|  
|$ShellFolder $|Der vollständige Pfad des Speicher Orts, an dem Visual Studio installiert wurde.|  
|$System $|Der Ordner "Windows\System32".|  
|$WINDIR $|Der Windows-Ordner.|  
  
 Wenn der Parser die Ersetzungs Zeichenfolge nicht erkennt oder den Wert eines Registrierungs Eintrags oder einer Umgebungsvariablen nicht ermitteln kann, führt er keine Ersetzung für diesen Teil der Zeichenfolge aus.
