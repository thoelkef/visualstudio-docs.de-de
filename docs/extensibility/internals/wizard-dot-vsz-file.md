---
title: "Assistenten (. VSZ)-Datei | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".vsz-Dateien"
  - "VSZ-Dateien"
  - "Assistenten, Dateien"
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Assistenten (. VSZ)-Datei
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die integrierte Entwicklungsumgebung \(IDE\) von .vsz\-Dateien Assistenten zu starten.  Diese .vsz\-Dateien enthalten Informationen, die die IDE verwendet, um zu ermitteln, welche vom Assistenten aufgerufen werden und welche Informationen an den Assistenten übergeben werden sollen.  
  
 Eine VSZ\-Datei handelt es sich um eine Version einer .ini\-formatted Textdatei, die keine Bereiche verfügt.  Die Informationen, die die IDE bekannt sind, werden am Anfang der Datei gespeichert.  Dies stellt einen Link zwischen dem Assistenten IDE\-Aufrufe und die Parameter, die in der IDE sind für den VSZ\-Datei übergeben werden sollen.  Der Rest der Datei enthält Parameter, die an den Assistenten beziehen und über die IDE erfasst werden und den jeweiligen Assistenten übergeben werden sollen.  
  
 Das folgende Beispiel zeigt den Inhalt einer VSZ\-Datei an.  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 Im Folgenden werden die Teile in der VSZ\-Datei.  
  
|Bestandteil|Beschreibung|  
|-----------------|------------------|  
|VSWizard|Der erste Parameter in der Datei handelt es sich um die Versionsnummer des Vorlagendatei formats.  Diese Versionsnummer muss 6.0, 7.0, 7.1 oder 8.0 sein.  Andere Zahlen können nicht gestartet werden und ein ungültiges Format von Fehlern führen.|  
|Assistent|Dieses Feld enthält die OLE ProgID des Assistenten oder alternativ eine GUID\-Zeichenfolgendarstellung der CLSID des Assistenten, der von der IDE erstellt wird.|  
|Param|Diese Bereiche sind optional.  Sie können beliebig viele nach Bedarf hinzufügen.|  
  
 Die Parameter ermöglichen die VSZ\-Datei, um zusätzliche benutzerdefinierte Parameter an den Assistenten übergeben wird.  Jeder Wert wird als Zeichenfolgenelement in einem Array Varianten an den Assistenten übergeben.  Weitere Informationen finden Sie unter [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md).  Weitere Informationen zum Erstellen einer VSZ\-Datei in der Entwicklung von benutzerdefinierten Assistenten finden Sie unter [VSZ\-Datei \(Projektsteuerung\)](/visual-cpp/ide/dot-vsz-file-project-control)verwendet  
  
 Um eine Gebietsschema\-ID der VSZ\-Datei hinzufügen, geben Sie `FALLBACK_LCID`\=xxxx an, in dem xxxx die Gebietsschema\-ID z. B. 1033 für Englisch ist.  Wenn `FALLBACK_LCID`\-Parameter definiert ist, verwendet der Assistent die bereitgestellte Fallback gebietsschema\-id, wenn die aktuelle ID nicht gefunden wird.  
  
## Siehe auch  
 [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)   
 [Assistenten](../../extensibility/internals/wizards.md)   
 [Beschreibung der Vorlage Verzeichnis \(. VSDIR\)\-Dateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)