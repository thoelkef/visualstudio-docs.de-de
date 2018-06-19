---
title: Benutzerdefinierte Parameter | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2fb61109a05b84eeb83b887ba0fc1a9f9fef299f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134336"
---
# <a name="custom-parameters"></a>Benutzerdefinierte Parameter
Benutzerdefinierte Parameter Steuerung der Arbeitsweise eines Assistenten, nachdem ein Assistent gestartet wurde. Eine verwandte VSZ-Datei enthält ein Array der benutzerdefinierten Parameter, die von der integrierten Entwicklungsumgebung (IDE) gepackt und beim Start des Assistenten als ein Array von Zeichenfolgen an den Assistenten übergeben werden. Der Assistent analysiert das Array von Zeichenfolgen und verwendet die Informationen zum Steuern der tatsächlichen Ausführung des Assistenten. Auf diese Weise kann anpassen, ein Assistenten Funktionalität abhängig vom Inhalt der VSZ-Datei.  
  
 Kontextparametern definieren andererseits, den Zustand des Projekts beim Start des Assistenten. Weitere Informationen finden Sie unter [Kontextparameter](../../extensibility/internals/context-parameters.md).  
  
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
  
 Der Autor der VSZ-Datei fügt die Werte der Parameter hinzu. Wenn ein Benutzer wählt **neues Projekt** oder **neues Element hinzufügen** auf das Menü Datei oder durch Rechtsklick auf ein Projekt in **Projektmappen-Explorer**, die IDE sammelt diese Werte in ein Array von Zeichenfolgen. Die IDE ruft dann des Projekts <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> Methode mit der <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> flag festlegen, und ruft die Projekt die <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> -Methode, die für das Ausführen des Assistenten und Zurückgeben des Ergebnisses zuständig ist.  
  
 Der Assistent ist verantwortlich für das Array von Zeichenfolgen zu analysieren und entsprechend auf die Zeichenfolgen fungiert. Auf diese Weise können Sie durch die Implementierung der benutzerdefinierten Parameter einem Assistenten erstellen, die eine Vielzahl von Funktionen ausführt. Das heißt, konnte ein Assistent drei verschiedene VSZ-Dateien verfügen. Jede Datei übergibt unterschiedliche Sätze von benutzerdefinierten Parametern zum Steuern des Verhaltens des Assistenten in verschiedenen Situationen.  
  
 Weitere Informationen finden Sie unter [Assistenten (. VSZ) Datei](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Kontextparameter](../../extensibility/internals/context-parameters.md)   
 [Assistenten](../../extensibility/internals/wizards.md)   
 [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)