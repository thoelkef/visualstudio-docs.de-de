---
title: Kontextparameter | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cb6646e917b4cb94b4cd0534b513d148490cf69d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="context-parameters"></a>Kontextparameter
In der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE), können Sie Assistenten zum Hinzufügen der **neues Projekt**, **neues Element hinzufügen**, oder **Sub-Projekt hinzufügen** Dialogfelder. Die hinzugefügten Assistenten stehen auf der **Datei** Menü oder über das Kontextmenü eines Projekts in **Projektmappen-Explorer**. Die IDE übergibt Kontextparameter für die Implementierung des Assistenten. Der Kontextparameter definieren den Zustand des Projekts aus, wenn die IDE des Assistenten aufgerufen.  
  
 Starten der IDE Assistenten durch Festlegen der <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> -Flag in der IDE-Aufruf an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> Methode für das Projekt. Wenn festgelegt ist, muss das Projekt wird die `IVsExtensibility::RunWizardFile` ausgeführt wird, indem der Name des registrierten Assistenten oder GUID und andere Kontextparameter, die von die IDE an sie übergeben.  
  
## <a name="context-parameters-for-new-project"></a>Kontextparameter für neues Projekt  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`WizardType`|Registriert die Assistenten-Typ (<xref:EnvDTE.Constants.vsWizardNewProject>) oder die GUID, der den Typ des Assistenten angibt. In der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Implementierung, die GUID für den Assistenten ist {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Eine Zeichenfolge, die eindeutige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projektname.|  
|`LocalDirectory`|Lokalen Speicherort der Projektdateien arbeiten.|  
|`InstallationDirectory`|Pfad des Verzeichnisses der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist die Installation.|  
|`FExclusive`|Boolean-Flag gibt an, dass das Projekt geöffneten Projektmappen schließen.|  
|`SolutionName`|Der Name der Projektmappendatei ohne den Verzeichnisteil oder die sln-Erweiterung. Der Name der SUO-Datei wird auch mit erstellt `SolutionName`. Wenn dieses Argument nicht um eine leere Zeichenfolge ist, verwendet der Assistent <xref:EnvDTE._Solution.Create%2A> vor dem Hinzufügen des Projekts mit <xref:EnvDTE._Solution.AddFromTemplate%2A>. Wenn dieser Name eine leere Zeichenfolge ist, verwenden Sie <xref:EnvDTE._Solution.AddFromTemplate%2A> ohne Aufruf <xref:EnvDTE._Solution.Create%2A>.|  
|`Silent`|Boolescher Wert, der angibt, ob der Assistent im Hintergrund ausgeführt werden soll als **Fertig stellen** geklickt wurden (`TRUE`).|  
  
## <a name="context-parameters-for-add-new-item"></a>Kontextparameter für hinzufügen neues Element  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`WizardType`|Registriert die Assistenten-Typ (<xref:EnvDTE.Constants.vsWizardAddItem>) oder die GUID, der den Typ des Assistenten angibt. In der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Implementierung, die GUID für den Assistenten ist {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Eine Zeichenfolge, die eindeutige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projektname.|  
|`ProjectItems`|Lokale Verzeichnis, in Projektdateien arbeiten.|  
|`ItemName`|Der Name des Elements, das hinzugefügt werden soll. Dieser Name ist der Standardname für die Datei oder den Dateinamen, die der Benutzer, von eingibt der **Elemente hinzufügen** (Dialogfeld). Der Name basiert auf die Flags, die in der VSDIR-Datei festgelegt werden. Der Name kann ein null-Wert sein.|  
|`InstallationDirectory`|Pfad des Verzeichnisses der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist die Installation.|  
|`Silent`|Boolescher Wert, der angibt, ob der Assistent im Hintergrund ausgeführt werden soll als **Fertig stellen** geklickt wurden (`TRUE`).|  
  
## <a name="context-parameters-for-add-sub-project"></a>Kontextparameter für Sub-Projekt hinzufügen  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`WizardType`|Registriert die Assistenten-Typ (<xref:EnvDTE.Constants.vsWizardAddSubProject>) oder die GUID, der den Typ des Assistenten angibt. In der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Implementierung, die GUID für den Assistenten ist {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Eine Zeichenfolge, die eindeutige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projektname.|  
|`ProjectItems`|Zeiger auf die `ProjectItems` Auflistung, die auf dem der Assistent ausgeführt wird. This-Zeiger wird an den Assistenten basierend auf der ausgewählten Projekthierarchie übergeben. Ein Benutzer einen Ordner, in dem das Element ablegen in der Regel auswählt und ruft dann des Projekts **Element hinzufügen** (Dialogfeld).|  
|`LocalDirectory`|Lokalen Speicherort der Projektdateien arbeiten.|  
|`ItemName`|Der Name des Elements, das hinzugefügt werden soll. Dieser Name ist der Standardname für die Datei oder den Dateinamen, die der Benutzer, von eingibt der **Elemente hinzufügen** (Dialogfeld). Der Name basiert auf die Flags, die in der VSDIR-Datei festgelegt werden. Der Name kann ein null-Wert sein.|  
|`InstallationDirectory`|Pfad des Verzeichnisses der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist die Installation.|  
|`Silent`|Boolescher Wert, der angibt, ob der Assistent im Hintergrund ausgeführt werden soll als **Fertig stellen** geklickt wurden (`TRUE`).|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)   
 [Assistenten](../../extensibility/internals/wizards.md)   
 [Assistenten (. VSZ)-Datei](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Kontextparameter für das Starten des Assistenten](http://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)