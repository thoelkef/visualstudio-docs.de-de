---
title: Kontextparameter | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 679bf567d2f44564d31d70b62c8663e665e1ea65
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697287"
---
# <a name="context-parameters"></a>Kontextparameter
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (IDE), können Sie die Assistenten zum Hinzufügen der **neues Projekt**, **neues Element hinzufügen**, oder **Sub-Projekt hinzufügen** Dialogfelder. Die hinzugefügten Assistenten stehen auf der **Datei** Menü oder per Rechtsklick auf ein Projekt in **Projektmappen-Explorer**. Die IDE übergibt Kontextparameter für die Implementierung des Assistenten. Der Kontextparameter definieren den Zustand des Projekts aus, wenn die IDE der Assistent ruft.  
  
 Starten der IDE Assistenten durch Festlegen der <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> -Kennzeichen in der IDE-Aufruf an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> Methode für das Projekt. Wenn festgelegt, muss das Projekt wird die `IVsExtensibility::RunWizardFile` Methode ausgeführt werden, mithilfe der Name des registrierten Assistenten "oder" GUID "und" anderen Kontextparameter, die von die IDE an sie übergeben.  
  
## <a name="context-parameters-for-new-project"></a>Kontextparameter für neues Projekt  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`WizardType`|Assistenten-Typ registriert (<xref:EnvDTE.Constants.vsWizardNewProject>) oder die GUID, der den Typ des Assistenten angibt. In der [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] -Implementierung, die GUID für den Assistenten ist {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Eine Zeichenfolge, die eindeutige [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Projektnamen.|  
|`LocalDirectory`|Speicherort der Projektdateien zu arbeiten.|  
|`InstallationDirectory`|Pfad des Verzeichnisses der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ist die Installation.|  
|`FExclusive`|Boolesches Flag gibt an, dass das Projekt geöffneten Projektmappen schließen.|  
|`SolutionName`|Der Name der Projektmappendatei ohne den Verzeichnisabschnitt oder die sln-Erweiterung. Die SUO-Dateiname wird auch erstellt, mit `SolutionName`. Wenn dieses Argument keine leere Zeichenfolge ist, verwendet der Assistent <xref:EnvDTE._Solution.Create%2A> vor dem Hinzufügen des Projekts mit <xref:EnvDTE._Solution.AddFromTemplate%2A>. Wenn dieser Name eine leere Zeichenfolge ist, verwenden Sie <xref:EnvDTE._Solution.AddFromTemplate%2A> ohne <xref:EnvDTE._Solution.Create%2A>.|  
|`Silent`|Boolescher Wert, der angibt, ob der Assistent im Hintergrund ausgeführt werden soll wie **Fertig stellen** geklickt wurden (`TRUE`).|  
  
## <a name="context-parameters-for-add-new-item"></a>Kontextparameter für hinzufügen neues Element  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`WizardType`|Assistenten-Typ registriert (<xref:EnvDTE.Constants.vsWizardAddItem>) oder die GUID, der den Typ des Assistenten angibt. In der [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] -Implementierung, die GUID für den Assistenten ist {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Eine Zeichenfolge, die eindeutige [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Projektnamen.|  
|`ProjectItems`|Lokale Pfad, der Arbeitsdateien-Projekt enthält.|  
|`ItemName`|Der Name des Elements, das hinzugefügt werden soll. Dieser Name ist entweder der Standardname für die Datei oder den Dateinamen, die der Benutzer, von eingibt der **Elemente hinzufügen** Dialogfeld. Der Name basiert auf den Flags, die in der VSDIR-Datei festgelegt werden. Der Name kann ein null-Wert sein.|  
|`InstallationDirectory`|Pfad des Verzeichnisses der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ist die Installation.|  
|`Silent`|Boolescher Wert, der angibt, ob der Assistent im Hintergrund ausgeführt werden soll wie **Fertig stellen** geklickt wurden (`TRUE`).|  
  
## <a name="context-parameters-for-add-sub-project"></a>Kontextparameter für Sub-Projekt hinzufügen  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`WizardType`|Assistenten-Typ registriert (<xref:EnvDTE.Constants.vsWizardAddSubProject>) oder die GUID, der den Typ des Assistenten angibt. In der [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] -Implementierung, die GUID für den Assistenten ist {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Eine Zeichenfolge, die eindeutige [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Projektnamen.|  
|`ProjectItems`|Zeiger auf die `ProjectItems` Auflistung, die auf dem der Assistent ausgeführt wird. This-Zeiger wird an den Assistenten, die basierend auf der ausgewählten Projekthierarchie übergeben. Ein Benutzer in der Regel wählt einen Ordner in dem das Element abgelegt werden sollen, und ruft dann des Projekts **Element hinzufügen** Dialogfeld.|  
|`LocalDirectory`|Speicherort der Projektdateien zu arbeiten.|  
|`ItemName`|Der Name des Elements, das hinzugefügt werden soll. Dieser Name ist entweder der Standardname für die Datei oder den Dateinamen, die der Benutzer, von eingibt der **Elemente hinzufügen** Dialogfeld. Der Name basiert auf den Flags, die in der VSDIR-Datei festgelegt werden. Der Name kann ein null-Wert sein.|  
|`InstallationDirectory`|Pfad des Verzeichnisses der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ist die Installation.|  
|`Silent`|Boolescher Wert, der angibt, ob der Assistent im Hintergrund ausgeführt werden soll wie **Fertig stellen** geklickt wurden (`TRUE`).|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)   
 [Assistenten](../../extensibility/internals/wizards.md)   
 [Assistenten (. VSZ)-Datei](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Kontextparameter zum Starten von Assistenten](https://msdn.microsoft.com/library/051a10f4-9e45-4604-b344-123044f33a24)
