---
title: Assistenten (. VSZ) Datei | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 15c07da8c41bcf5fc65e35e1347095b2e8d8415e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142876"
---
# <a name="wizard-vsz-file"></a>Assistenten (. VSZ)-Datei
Die integrierte Entwicklungsumgebung (IDE) verwendet .vsz-Dateien um den Assistenten zu starten. Diese VSZ-Dateien enthalten Informationen, die die IDE verwendet, um zu bestimmen, welche Assistenten aufrufen und welche Informationen an den Assistenten übergeben.  
  
 VSZ-Datei ist eine Version einer INI-formatiertem Text-Datei, die keine Abschnitte aufweist. Informationen, die bekanntermaßen von der IDE werden am Anfang der Datei gespeichert. Dies bietet eine Verknüpfung zwischen den Assistenten, den die IDE aufruft und die Parameter, die in der VSZ-Datei in der IDE übergeben werden. Der Rest der Datei enthält Parameter, um den Assistenten spezifisch sind und die von der IDE gesammelt werden kann und an den bestimmten Assistenten übergeben.  
  
 Das folgende Beispiel zeigt den Inhalt einer VSZ-Datei.  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 Im folgenden werden die Teile in der VSZ-Datei.  
  
|Segment|Beschreibung|  
|----------|-----------------|  
|VSWizard|Der erste Parameter in der Datei ist die Versionsnummer des Vorlagendateiformats. Diese Versionsnummer muss 6.0, 7.0, 7.1 oder 8.0. Andere Zahlen können nicht gestartet werden und verursacht einen Fehler Ungültiges Format.|  
|Assistent|Dieses Feld enthält die OLE ProgID des Assistenten oder alternativ eine GUID-Zeichenfolgendarstellung die CLSID des Assistenten, der gleichzeitig von der IDE erstellt wird.|  
|Parameter|Diese Teile sind optional. Sie können so viele wie erforderlich hinzufügen.|  
  
 Der Typparameter ermöglichen es der VSZ-Datei können zusätzliche benutzerdefinierte Parameter an den Assistenten übergeben. Jeder Wert wird als ein Zeichenfolgenelement in ein Array von Variant-Assistenten für den übergeben. Weitere Informationen finden Sie unter [benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md). Weitere Informationen dazu, wie eine VSZ-Datei in die Entwicklung von benutzerdefinierten Assistenten verwenden, finden Sie unter [. VSZ-Datei (Projektsteuerung)](/cpp/ide/dot-vsz-file-project-control)  
  
 Um eine Standard-Gebietsschema-ID VSZ-Datei hinzuzufügen, geben Sie `FALLBACK_LCID`= Xxxx, wobei Xxxx die Gebietsschema-ID, z. B. 1033 für Englisch. Wenn `FALLBACK_LCID` Parameter definiert ist, wird der Assistent verwendet die angegebene alternative Gebietsschema-ID an, wenn die aktuelle ID nicht gefunden wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)   
 [Assistenten](../../extensibility/internals/wizards.md)   
 [Dateien zur Beschreibung des Vorlagenverzeichnisses (VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)