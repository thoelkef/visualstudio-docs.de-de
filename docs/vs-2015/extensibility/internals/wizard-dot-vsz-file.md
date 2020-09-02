---
title: Assistent (. VSZ-Datei | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab1adde4c7018f136f47769e16a8ce2fedf72c93
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687664"
---
# <a name="wizard-vsz-file"></a>Assistentendatei (VSZ)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) verwendet VSZ-Dateien, um Assistenten zu starten. Diese VSZ-Dateien enthalten Informationen, die von der IDE verwendet werden, um zu bestimmen, welcher Assistent aufgerufen werden soll und welche Informationen an den Assistenten übergeben werden.  
  
 Eine VSZ-Datei ist eine Version einer. ini-formatierten Textdatei, die keine Abschnitte enthält. Die der IDE bekannten Informationen werden am Anfang der Datei gespeichert. Dadurch wird ein Link zwischen dem Assistenten, der von der IDE aufgerufen wird, und den Parametern, die sich in der VSZ-Datei befinden, zum Übertragen der IDE bereitstellt. Der Rest der Datei enthält Parameter, die für den Assistenten spezifisch sind und von der IDE gesammelt und an den jeweiligen Assistenten übergeben werden.  
  
 Das folgende Beispiel zeigt den Inhalt einer VSZ-Datei.  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 Im folgenden werden die Teile der VSZ-Datei angezeigt.  
  
|Teil|BESCHREIBUNG|  
|----------|-----------------|  
|VsWizard|Der erste Parameter in der Datei ist die Versionsnummer des Vorlagen Datei Formats. Diese Versionsnummer muss 6,0, 7,0, 7,1 oder 8,0 lauten. Andere Zahlen können nicht gestartet werden und führen zu einem ungültigen Formatierungs Fehler.|  
|Assistent|Dieses Feld enthält die OLE-ProgID des Assistenten oder alternativ eine GUID-Zeichen folgen Darstellung der CLSID des Assistenten, der von der IDE coerstellt wird.|  
|Parameter|Diese Komponenten sind optional. Sie können beliebig viele Anforderungen hinzufügen.|  
  
 Mit den Parametern kann die VSZ-Datei zusätzliche benutzerdefinierte Parameter an den Assistenten übergeben. Jeder Wert wird als Zeichen folgen Element in einem Array von Varianten an den Assistenten übermittelt. Weitere Informationen finden Sie unter [benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md). Informationen zur Verwendung einer VSZ-Datei in der Entwicklung von benutzerdefinierten Assistenten finden Sie unter [. VSZ-Datei (Projektsteuerung)](https://msdn.microsoft.com/library/b8678fee-6795-46d1-9338-48b22d5e9207)  
  
 Wenn Sie der VSZ-Datei eine Standard-Gebiets Schema-ID hinzufügen möchten, geben Sie `FALLBACK_LCID` = xxxx an, wobei xxxx die Gebiets Schema-ID ist, z. b. 1033 für Englisch. Wenn der `FALLBACK_LCID` Parameter definiert ist, verwendet der Assistent die angegebene Fall Back-Gebiets Schema-ID, wenn die aktuelle ID nicht gefunden wurde.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)   
 [The](../../extensibility/internals/wizards.md)   
 [Dateien zur Beschreibung des Vorlagenverzeichnisses (VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
