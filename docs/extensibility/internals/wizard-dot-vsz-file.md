---
title: Assistenten (. VSZ) Datei | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: 9
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 3b1ee351d5fbe66a5d74c07c0a7e5a60661d7fcb
ms.lasthandoff: 04/05/2017

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
