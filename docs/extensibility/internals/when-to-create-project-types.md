---
title: Wenn Projekttypen erstellen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b532ad4e72fb15cd9409c362259347f6f3833d2e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="when-to-create-project-types"></a>Wenn Projekttypen erstellen
Erstellen einen neuen Projekttyp bietet eine Grundlage für die Anpassung von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] für Ihre Benutzer. Erstellen einen neuen Projekttyp ist jedoch nicht erforderlich, damit alle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Anpassungen. Die folgenden Richtlinien können Ihnen helfen zu bestimmen, ob für ein neuen Projekttyp für Ihr Szenario erforderlich ist.  
  
## <a name="create-a-new-project-type"></a>Erstellen Sie einen neuen Projekttyp  
 Sie müssen einen Projekttyp erstellen, wenn Sie anpassen möchten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fungieren in mindestens einer der folgenden Methoden:  
  
-   Build beteiligt sein, bereitstellen, Konfigurationen und Datenquellen-Steuerelements.  
  
-   Angebot debugging-Unterstützung.  
  
-   Anzeige der Projektelemente im **Projektmappen-Explorer**.  
  
-   Verwenden der **Projekt öffnen** oder **neues Projekt** (Dialogfeld).  
  
-   Projekt Schachtelung zu unterstützen.  
  
## <a name="extend-an-existing-project-type"></a>Erweitern eines vorhandenen Projekttyps  
 Möglicherweise möchten Sie einen neuen Projekttyp erstellen, das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] auf folgende Weise ändern oder erweitern das Verhalten eines vorhandenen Projekts-Typs, z. B. Ändern des Buildprozesses für [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekte:  
  
-   Arbeiten Sie mit mehreren Dateien als einzelne Einheit.  
  
-   Zeigen Sie eine einzelne Datei als eine Hierarchie von untergeordneten Elementen.  
  
-   Zeigen Sie einen Befehlskontext um Editoren.  
  
-   Zeigen Sie einen Dienstkontext für Editoren.  
  
## <a name="use-an-existing-project-type"></a>Verwenden eines vorhandenen Projekttyps  
 Erstellen eines neuen Projekts ist in einigen Fällen nicht erforderlich. Die folgende Tabelle zeigt die Aufgaben, denen Sie nicht verfügen, erstellen Sie ein Projekt für.  
  
|Aufgabe|Beschreibung|  
|----------|-----------------|  
|Behandeln von Kommentaren|Alle VSPackage kann Befehle behandeln.|  
|Erstellen eines Editors|Benutzerdefinierte Editoren können registriert werden. Weitere Informationen finden Sie unter [Dokument- und Editoren](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc).|  
|Besitzer von windows|Sie können Tool-und Dokumentfenster erstellen, ohne einen neuen Projekttyp hinzufügen.|  
|Verfügbarmachen von Eigenschaften im Eigenschaftenfenster|Alle Objekte können Eigenschaften verfügbar machen.|  
  
## <a name="create-a-project-subtype"></a>Erstellen Sie einen Projektuntertyp  
 Sie können Projekt Untertypen verwenden, um ein verwaltetes Projekt zu erweitern, ohne einen neuen Projekttyp erstellen zu müssen. Projekt Untertypen COM Aggregation verwenden, um verwaltete Projekte in Microsoft geschrieben zu erweitern [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] oder [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Mit COM-Aggregation können Großteil der Implementierung System verwalteten Projekt wiederverwenden und für ein bestimmtes Szenario durch Aggregation und die Verwendung von Schnittstellen unterstützen weiterhin anpassen. Weitere Informationen zum Projekt Untertypen, finden Sie unter [Projekt Untertypen](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Dokumentfenster und Editoren](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc)   
 [Prüfliste: Erstellen neuen Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)