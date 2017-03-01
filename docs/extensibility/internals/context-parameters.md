---
title: Kontextparameter | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
caps.latest.revision: 13
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 143a8738f2eb6517c1642eafd2b9629e0fa8f84d
ms.lasthandoff: 02/22/2017

---
# <a name="context-parameters"></a>Kontextparameter
In der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE), können Sie Assistenten zum Hinzufügen der **neues Projekt**, **neues Element hinzufügen**, oder **Sub-Projekt hinzufügen** Dialogfelder. Die hinzugefügten Assistenten stehen auf der **Datei** Menü oder indem Sie ein Projekt in **Projektmappen-Explorer**. Die IDE übergibt Kontextparameter für die Implementierung des Assistenten. Die Kontextparameter definieren den Status des Projekts aus, wenn die IDE der Assistent ruft.  
  
 Starten der IDE Assistenten durch Festlegen der <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>-Flag in der IDE-Aufruf an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>Methode für das Projekt.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> </xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> Wenn festgelegt ist, muss das Projekt wird der `IVsExtensibility::RunWizardFile` ausgeführt wird, indem der Name des registrierten Assistenten oder GUID und andere Kontextparameter, die die IDE an sie übergeben.  
  
## <a name="context-parameters-for-new-project"></a>Kontextparameter für neues Projekt  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`WizardType`|Assistenten-Typ registriert (<xref:EnvDTE.Constants.vsWizardNewProject>) oder die GUID, der den Typ des Assistenten angibt.</xref:EnvDTE.Constants.vsWizardNewProject> In der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] -Implementierung, die GUID für den Assistenten ist {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Eine Zeichenfolge, die den eindeutigen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projektname.|  
|`LocalDirectory`|Der lokale Pfad der Projektdateien arbeiten.|  
|`InstallationDirectory`|Pfad des Verzeichnisses der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist die Installation.|  
|`FExclusive`|Boolesches Flag gibt an, dass das Projekt geöffneten Projektmappen schließen soll.|  
|`SolutionName`|Der Name der Projektmappendatei ohne den Verzeichnisabschnitt oder die sln-Erweiterung. Der Name der SUO-Datei wird auch erstellt, mithilfe von `SolutionName`. Wenn dieses Argument nicht um eine leere Zeichenfolge ist, verwendet der Assistent <xref:EnvDTE._Solution.Create%2A>vor dem Hinzufügen des Projekts mit <xref:EnvDTE._Solution.AddFromTemplate%2A></xref:EnvDTE._Solution.AddFromTemplate%2A> </xref:EnvDTE._Solution.Create%2A> Wenn dieser Name eine leere Zeichenfolge ist, verwenden Sie, <xref:EnvDTE._Solution.AddFromTemplate%2A>ohne Aufruf von <xref:EnvDTE._Solution.Create%2A>.</xref:EnvDTE._Solution.Create%2A> </xref:EnvDTE._Solution.AddFromTemplate%2A>|  
|`Silent`|Boolescher Wert, der angibt, ob der Assistent unbeaufsichtigt ausgeführt werden soll als **Fertig stellen** geklickt wurden (`TRUE`).|  
  
## <a name="context-parameters-for-add-new-item"></a>Kontextparameter für hinzufügen neues Element  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`WizardType`|Assistenten-Typ registriert (<xref:EnvDTE.Constants.vsWizardAddItem>) oder die GUID, der den Typ des Assistenten angibt.</xref:EnvDTE.Constants.vsWizardAddItem> In der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] -Implementierung, die GUID für den Assistenten ist {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Eine Zeichenfolge, die den eindeutigen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projektname.|  
|`ProjectItems`|Der lokale Pfad, die ordnungsgemäße Projektdateien enthält.|  
|`ItemName`|Der Name des Elements, das hinzugefügt werden soll. Dieser Name ist der Standardname für die Datei oder den Dateinamen, die der Benutzer, von eingibt der **Elemente hinzufügen** Dialogfeld. Der Name basiert auf der Flags, die in der VSDIR-Datei festgelegt werden. Der Name kann ein null-Wert sein.|  
|`InstallationDirectory`|Pfad des Verzeichnisses der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist die Installation.|  
|`Silent`|Boolescher Wert, der angibt, ob der Assistent unbeaufsichtigt ausgeführt werden soll als **Fertig stellen** geklickt wurden (`TRUE`).|  
  
## <a name="context-parameters-for-add-sub-project"></a>Kontextparameter zum Sub-Projekt hinzufügen  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`WizardType`|Assistenten-Typ registriert (<xref:EnvDTE.Constants.vsWizardAddSubProject>) oder die GUID, der den Typ des Assistenten angibt.</xref:EnvDTE.Constants.vsWizardAddSubProject> In der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] -Implementierung, die GUID für den Assistenten ist {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Eine Zeichenfolge, die den eindeutigen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projektname.|  
|`ProjectItems`|Zeiger auf die `ProjectItems` Auflistung, die auf dem der Assistent ausgeführt wird. Dieser Zeiger wird an dem Assistenten entsprechend der ausgewählten Projekthierarchie übergeben. Ein Benutzer in der Regel wählt einen Ordner zum Speichern des Elements und ruft dann des Projekts **hinzufügen** Dialogfeld.|  
|`LocalDirectory`|Der lokale Pfad der Projektdateien arbeiten.|  
|`ItemName`|Der Name des Elements, das hinzugefügt werden soll. Dieser Name ist der Standardname für die Datei oder den Dateinamen, die der Benutzer, von eingibt der **Elemente hinzufügen** Dialogfeld. Der Name basiert auf der Flags, die in der VSDIR-Datei festgelegt werden. Der Name kann ein null-Wert sein.|  
|`InstallationDirectory`|Pfad des Verzeichnisses der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist die Installation.|  
|`Silent`|Boolescher Wert, der angibt, ob der Assistent unbeaufsichtigt ausgeführt werden soll als **Fertig stellen** geklickt wurden (`TRUE`).|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)   
 [Assistenten](../../extensibility/internals/wizards.md)   
 [Assistenten (. VSZ)-Datei](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Kontextparameter zum Starten von Assistenten](http://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
