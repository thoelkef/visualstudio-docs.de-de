---
title: "Benutzerdefinierte Parameter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Assistenten, benutzerdefinierte Parameter"
  - "Benutzerdefinierte Parameter"
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Benutzerdefinierte Parameter
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Benutzerdefinierte Parameter steuern die Ausführung eines Assistenten, nachdem ein Assistent gestartet wurde.  Eine verwandte VSZ\-Datei enthält ein Array von benutzerdefinierten Parametern, die von der integrierten Entwicklungsumgebung \(IDE\) an den Assistenten übergeben und als Zeichenfolgenarray gepackt werden, wenn der Assistent gestartet wird.  Der Assistent dann analysiert das Zeichenfolgenarray und verwendet die Informationen, um den tatsächlichen Vorgang des Assistenten zu steuern.  Auf diese Weise kann ein Assistent Funktionen abhängig vom Inhalt der VSZ\-Datei anpassen.  
  
 Kontextparameter definieren hingegen den Stand des Projekts, wenn der Assistent gestartet wird.  Weitere Informationen finden Sie unter [Kontextparameter](../../extensibility/internals/context-parameters.md).  
  
 Im Folgenden finden Sie ein Beispiel für eine VSZ\-Datei mit benutzerdefinierten Parameter verfügt:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 Der Autor der VSZ\-Datei fügt die Werte der Parameter hinzu.  Wenn ein Benutzer **Neues Projekt** oder **Neues Element hinzufügen** im Menü Datei auswählen oder indem er auf ein Projekt in **Projektmappen\-Explorer**mit der rechten Maustaste klickt, werden die IDE diese Werte in ein Zeichenfolgenarray.  Die IDE ruft dann die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>\-Methode des Projekts mit dem <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>\-Flags festgelegt, und das Projekt <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> ruft die Methode auf, die zum Ausführen des Assistenten und die Rückgabe des Ergebnisses zuständig ist.  
  
 Der Assistent ist für das Array von Zeichenfolgen geeignet analysieren und nach Zeichenfolgen werden.  Auf diese Weise indem Sie benutzerdefinierte Parameter implementieren, können Sie einen Assistenten erstellen, der eine Vielzahl von Funktionen ausführt.  Das heißt, kann ein Assistent drei verschiedene .vsz\-Dateien haben.  Jede Datei führt verschiedene Sätze von benutzerdefinierten Parameter, um das Verhalten des Assistenten in verschiedenen Situationen zu steuern.  
  
 Weitere Informationen finden Sie unter [Assistenten \(. VSZ\)\-Datei](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Kontextparameter](../../extensibility/internals/context-parameters.md)   
 [Assistenten](../../extensibility/internals/wizards.md)   
 [Assistenten \(. VSZ\)\-Datei](../../extensibility/internals/wizard-dot-vsz-file.md)