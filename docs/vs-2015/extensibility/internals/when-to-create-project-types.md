---
title: Gründe für das Erstellen von Projekttypen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 682fc88fb616fbe2617fe6d336a35bf6fbc30e9f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946724"
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
|Erstellen eines Editors|Benutzerdefinierte Editoren können registriert werden. Weitere Informationen finden Sie unter [Dokument Windows und Editoren](http://msdn.microsoft.com/603625e1-62b6-413a-bc44-089346e166bc).|  
|Besitzer von windows|Sie können sowohl Tool-und Dokumentfenster erstellen, ohne dass einen neuer Projekttyp hinzugefügt.|  
|Verfügbarmachen von Eigenschaften im Eigenschaftenfenster|Alle Objekte können Eigenschaften verfügbar machen.|  
  
## <a name="create-a-project-subtype"></a>Erstellen von einem Projektuntertyp  
 Sie können die Projektuntertypen verwenden, um ein verwaltetes Projekt zu erweitern, ohne einen neuen Projekttyp erstellen zu müssen. Projektuntertypen com-Aggregation verwenden Sie zum Erweitern von verwalteter Projekten, die bei Microsoft geschrieben [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] oder [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Mit COM-Aggregation können ein Großteil der systemimplementierung verwaltetes Projekt wiederverwenden und dennoch für ein bestimmtes Szenario durch die Aggregation und die Verwendung von unterstützende Schnittstellen anpassen. Weitere Informationen zu Projektuntertypen, finden Sie unter [Projektuntertypen](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Dokument Windows und Editoren](http://msdn.microsoft.com/603625e1-62b6-413a-bc44-089346e166bc)   
 [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
