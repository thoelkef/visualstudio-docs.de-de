---
title: Benutzerdefinierte Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8bb8a1861d6162e73906d74250f738ff96b9a505
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757912"
---
# <a name="custom-parameters"></a>Benutzerdefinierte Parameter
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Benutzerdefinierte Parameter steuern den Betrieb des einen Assistenten, nachdem ein Assistent gestartet wurde. Eine verwandte VSZ-Datei enthält ein Array von benutzerdefinierten Parametern, die von der integrierten Entwicklungsumgebung (IDE) verpackt und an den Assistenten als ein Array von Zeichenfolgen übergeben wird, wenn der Assistent gestartet wird. Der Assistent analysiert das Array von Zeichenfolgen und verwendet die Informationen zum Steuern der tatsächlichen Ausführung des Assistenten. Auf diese Weise kann ein Assistenten Funktionalität je nach den Inhalten der VSZ-Datei anpassen.  
  
 Kontextparameter, definieren den Zustand des Projekts auf der anderen Seite, beim Starten des Assistenten. Weitere Informationen finden Sie unter [Kontextparameter](../../extensibility/internals/context-parameters.md).  
  
 Es folgt ein Beispiel für eine VSZ-Datei, die benutzerdefinierten Parameter verfügt:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 Der Autor der VSZ-Datei fügt die Werte der Parameter hinzu. Wenn ein Benutzer auswählt **neues Projekt** oder **neues Element hinzufügen** auf das Menü "Datei" oder durch Rechtsklick auf ein Projekt in **Projektmappen-Explorer**, die IDE sammelt diese Werte in ein Array von Zeichenfolgen. Die IDE ruft dann des Projekts <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> -Methode mit der <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> flag Satz und die projektaufrufe der <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> -Methode, die für den Assistenten auszuführen und das Ergebnis zuständig ist.  
  
 Der Assistent ist verantwortlich für das Array von Zeichenfolgen zu analysieren und, die auf die Zeichenfolgen entsprechend. Auf diese Weise können Sie durch die Implementierung von benutzerdefinierter Parameters einen Assistenten erstellen, die eine Vielzahl von Funktionen ausführt. Anders gesagt kann ein Assistent drei verschiedene VSZ-Dateien aufweisen. Jede Datei werden verschiedene Sätze von benutzerdefinierten Parametern zum Steuern des Verhaltens des Assistenten in verschiedenen Situationen übergeben.  
  
 Weitere Informationen finden Sie unter [Assistenten (. VSZ) Datei](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Kontextparameter](../../extensibility/internals/context-parameters.md)   
 [Assistenten](../../extensibility/internals/wizards.md)   
 [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)

