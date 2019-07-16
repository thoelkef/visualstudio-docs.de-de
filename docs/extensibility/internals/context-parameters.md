---
title: Kontextparameter | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ddbd8084da150e47fdbe350770ea5e6bdb7e28d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335595"
---
# <a name="context-parameters"></a>Kontextparameter
In der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE), können Sie die Assistenten zum Hinzufügen der **neues Projekt**, **neues Element hinzufügen**, oder **Sub-Projekt hinzufügen** Dialogfelder. Die hinzugefügten Assistenten stehen auf der **Datei** Menü oder per Rechtsklick auf ein Projekt in **Projektmappen-Explorer**. Die IDE übergibt Kontextparameter für die Implementierung des Assistenten. Der Kontextparameter definieren den Zustand des Projekts aus, wenn die IDE der Assistent ruft.

 Starten der IDE Assistenten durch Festlegen der <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> -Kennzeichen in der IDE-Aufruf an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> Methode für das Projekt. Wenn festgelegt, muss das Projekt wird die `IVsExtensibility::RunWizardFile` Methode ausgeführt werden, mithilfe der Name des registrierten Assistenten "oder" GUID "und" anderen Kontextparameter, die von die IDE an sie übergeben.

## <a name="context-parameters-for-new-project"></a>Kontextparameter für neues Projekt

| Parameter | Beschreibung |
|-------------------------| - |
| `WizardType` | Assistenten-Typ registriert (<xref:EnvDTE.Constants.vsWizardNewProject>) oder die GUID, der den Typ des Assistenten angibt. In der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] -Implementierung, die GUID für den Assistenten ist {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Eine Zeichenfolge, die eindeutige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projektnamen. |
| `LocalDirectory` | Speicherort der Projektdateien zu arbeiten. |
| `InstallationDirectory` | Pfad des Verzeichnisses der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist die Installation. |
| `FExclusive` | Boolesches Flag, die angibt, dass das Projekt geöffneten Projektmappen schließen. |
| `SolutionName` | Name der Projektmappendatei ohne den Verzeichnisabschnitt oder *sln* Erweiterung. Die *suo* Dateiname wird auch erstellt, mit `SolutionName`. Wenn dieses Argument keine leere Zeichenfolge ist, verwendet der Assistent <xref:EnvDTE._Solution.Create%2A> vor dem Hinzufügen des Projekts mit <xref:EnvDTE._Solution.AddFromTemplate%2A>. Wenn dieser Name eine leere Zeichenfolge ist, verwenden Sie <xref:EnvDTE._Solution.AddFromTemplate%2A> ohne <xref:EnvDTE._Solution.Create%2A>. |
| `Silent` | Boolescher Wert, der angibt, ob der Assistent im Hintergrund ausgeführt werden soll wie **Fertig stellen** geklickt wurden (`TRUE`). |

## <a name="context-parameters-for-add-new-item"></a>Kontextparameter für neues Element hinzufügen

| Parameter | Beschreibung |
|-------------------------| - |
| `WizardType` | Assistenten-Typ registriert (<xref:EnvDTE.Constants.vsWizardAddItem>) oder die GUID, der den Typ des Assistenten angibt. In der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] -Implementierung, die GUID für den Assistenten ist {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Eine Zeichenfolge, die eindeutige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projektnamen. |
| `ProjectItems` | Lokale Pfad, der Arbeitsdateien-Projekt enthält. |
| `ItemName` | Der Name des Elements, das hinzugefügt werden soll. Dieser Name ist entweder der Standardname für die Datei oder den Dateinamen, die der Benutzer, von eingibt der **Elemente hinzufügen** Dialogfeld. Der Name basiert darauf, dass die Flags, die auf die *VSDIR* Datei. Der Name kann ein null-Wert sein. |
| `InstallationDirectory` | Pfad des Verzeichnisses der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist die Installation. |
| `Silent` | Boolescher Wert, der angibt, ob der Assistent im Hintergrund ausgeführt werden soll wie **Fertig stellen** geklickt wurden (`TRUE`). |

## <a name="context-parameters-for-add-sub-project"></a>Kontextparameter für Sub-Projekt hinzufügen

| Parameter | Beschreibung |
|-------------------------| - |
| `WizardType` | Assistenten-Typ registriert (<xref:EnvDTE.Constants.vsWizardAddSubProject>) oder die GUID, der den Typ des Assistenten angibt. In der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] -Implementierung, die GUID für den Assistenten ist {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Eine Zeichenfolge, die eindeutige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projektnamen. |
| `ProjectItems` | Zeiger auf die `ProjectItems` Auflistung, die auf dem der Assistent ausgeführt wird. This-Zeiger wird an den Assistenten, die basierend auf der ausgewählten Projekthierarchie übergeben. Ein Benutzer in der Regel wählt einen Ordner in dem das Element abgelegt werden sollen, und ruft dann des Projekts **Element hinzufügen** Dialogfeld. |
| `LocalDirectory` | Speicherort der Projektdateien zu arbeiten. |
| `ItemName` | Der Name des Elements, das hinzugefügt werden soll. Dieser Name ist entweder der Standardname für die Datei oder den Dateinamen, die der Benutzer, von eingibt der **Elemente hinzufügen** Dialogfeld. Der Name basiert darauf, dass die Flags, die auf die *VSDIR* Datei. Der Name kann ein null-Wert sein. |
| `InstallationDirectory` | Pfad des Verzeichnisses der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Installation. |
| `Silent` | Boolescher Wert, der angibt, ob der Assistent im Hintergrund ausgeführt werden soll wie **Fertig stellen** geklickt wurden (`TRUE`). |

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)
- [Assistenten](../../extensibility/internals/wizards.md)
- [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Kontextparameter zum Starten von Assistenten](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)