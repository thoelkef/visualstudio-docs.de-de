---
title: "Problembehandlung bei Ausnahmen: System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHWRTTrackingProfileDeserialization"
helpviewer_keywords: 
  - "System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException-Ausnahme"
  - "TrackingProfileDeserializationException-Ausnahme"
ms.assetid: ce8fe4c1-43e3-4930-947e-74b8d94f32bf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException
Wenn ein XML\-Dokument von einem <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException> nicht in ein <xref:System.Workflow.Runtime.Tracking.TrackingProfile> deserialisiert werden kann, wird eine <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer>\-Ausnahme ausgelöst.  
  
## Hinweise  
 Wenn der <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> diese Ausnahme auslöst, wird eine Meldung ausgegeben, die den Grund für die Ausnahme beschreibt. In manchen Fällen liefert der <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> eine Liste mit Validierungsfehlern und Warnungen, die beim Versuch, das <xref:System.Workflow.Runtime.Tracking.TrackingProfile> zu deserialisieren, gefunden wurden. Wird eine solche Liste bereitgestellt, enthält diese die <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException.ValidationEventArgs%2A>\-Eigenschaft.  
  
## Siehe auch  
 <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)