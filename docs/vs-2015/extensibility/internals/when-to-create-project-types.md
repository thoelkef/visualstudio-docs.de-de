---
title: Gründe für das Erstellen von Projekttypen | Microsoft-Dokumentation
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
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 98dd3f0058e2dacd1a6ab8ed3fc048dfd2e6397e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245400"
---
# <a name="when-to-create-project-types"></a>Gründe für das Erstellen von Projekttypen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Erstellen einen neuen Projekttyp bildet die Grundlage für Anpassung [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] für Ihre Benutzer. Erstellen einen neuen Projekttyp ist jedoch nicht erforderlich, damit alle [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Anpassungen. Die folgenden Richtlinien sollten leichter bestimmen, ob ein neuer Projekttyp für Ihr Szenario erforderlich ist.  
  
## <a name="create-a-new-project-type"></a>Erstellen Sie einen neuen Projekttyp  
 Sie müssen einen Projekttyp erstellen, wenn Sie anpassen möchten [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , die in eine oder mehrere der folgenden Methoden verwendet:  
  
-   Teilnahme an Build, bereitstellen, Konfigurationen und Datenquellen-Steuerelement.  
  
-   Bieten Sie Unterstützung für Remotedebuggen.  
  
-   Anzeigen der Projektelemente im **Projektmappen-Explorer**.  
  
-   Verwenden der **geöffneten Projekt** oder **neues Projekt** Dialogfeld.  
  
-   Schachtelung von Projekt zu unterstützen.  
  
## <a name="extend-an-existing-project-type"></a>Erweitern Sie einen vorhandenen Projekttyp  
 Möglicherweise möchten Sie einen neuen Projekttyp zu erstellen, können [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] auf folgende Weise ändern oder erweitern das Verhalten eines vorhandenen Projekts-Typs, z. B. die Änderung des Buildprozesses für [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] Projekte:  
  
-   Arbeiten Sie mit mehreren Dateien als einzelne Einheit ein.  
  
-   Eine einzelne Datei als Hierarchie von untergeordneten Elementen anzeigen.  
  
-   Zeigen Sie einen Befehlskontext um Editoren.  
  
-   Zeigen Sie einen Dienstkontext für Editoren an.  
  
## <a name="use-an-existing-project-type"></a>Verwenden Sie einen vorhandenen Projekttyp  
 Erstellen eines neuen Projekts ist manchmal nicht erforderlich. Die folgende Tabelle zeigt die Aufgaben, denen Sie nicht, erstellen Sie einen Projekttyp für verfügen.  
  
|Aufgabe|Beschreibung|  
|----------|-----------------|  
|Behandeln von Kommentaren|Jedem VSPackage kann Befehle verarbeiten.|  
|Erstellen eines Editors|Benutzerdefinierte Editoren können registriert werden. Weitere Informationen finden Sie unter [Dokument Windows und Editoren](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc).|  
|Besitzer von windows|Sie können sowohl Tool-und Dokumentfenster erstellen, ohne dass einen neuer Projekttyp hinzugefügt.|  
|Verfügbarmachen von Eigenschaften im Eigenschaftenfenster|Alle Objekte können Eigenschaften verfügbar machen.|  
  
## <a name="create-a-project-subtype"></a>Erstellen von einem Projektuntertyp  
 Sie können die Projektuntertypen verwenden, um ein verwaltetes Projekt zu erweitern, ohne einen neuen Projekttyp erstellen zu müssen. Projektuntertypen com-Aggregation verwenden Sie zum Erweitern von verwalteter Projekten, die bei Microsoft geschrieben [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] oder [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Mit COM-Aggregation können ein Großteil der systemimplementierung verwaltetes Projekt wiederverwenden und dennoch für ein bestimmtes Szenario durch die Aggregation und die Verwendung von unterstützende Schnittstellen anpassen. Weitere Informationen zu Projektuntertypen, finden Sie unter [Projektuntertypen](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Dokument Windows und Editoren](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc)   
 [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

