---
title: "Wenig virtueller Arbeitsspeicher | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aec803b1-9d76-46bb-8f14-8c63d80112a5
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Wenig virtueller Arbeitsspeicher
Diese Meldung wird angezeigt, wenn wenig virtueller Arbeitsspeicher verfügbar ist und [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nicht mehr reagiert.  Allerdings tritt dieser Fehler nicht auf, wenn der virtuelle Speicher auf dem Computer niedrig ist, sondern wenn [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nicht genügend Adressraum zur Verfügung steht.  Dieser Fehler tritt am häufigsten auf Computern mit 32\-Bit\-Betriebssystemen auf, die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auf einen Adressraum von 2 GB beschränken.  Wenn Sie mit 32\-Bit\-Prozessen arbeiten, kann die App nur 4 GB Arbeitsspeicher \(2^32 Bits\) adressieren.  Allerdings reservieren 32\-Bit\-Versionen von Windows 2 GB des virtuellen Adressraums eines Prozesses für interne Zwecke \(z. B. für das Arbeiten mit der Grafikkarte des Computers oder anderen Systemtreibern\).  Daher kann der 32\-Bit\-Prozess nur 2 GB für seine internen Zwecke verwenden.  Benutzer können den \/3GB\- Schalter setzen, um sicherzustellen, dass Windows nur 1 GB für eigene Zwecke reserviert und 3 GB dem Prozess zuteilt.  In den meisten Fällen nimmt die Leistung bei einer Begrenzung auf nur 1 GB für Windows nicht ab.  
  
 Auf Systemen, die 64\-Bit\-Versionen von Windows ausführen, tritt dieser Fehler selten auf, da der Prozess die gesamten 4 GB an Adressraum verwenden und Windows 64\-Bit\-Speicheradressen zum Arbeiten mit den Hardware\- und Systemtreibern verwenden kann.  Die Arbeitsspeicherauslastung kann jedoch 3 GB oder sogar 4 GB überschreiten, wenn [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Datasets verarbeitet.  Weitere Informationen finden Sie unter [Visual Studio: Why is there no 64 bit version? \(yet\)](http://go.microsoft.com/fwlink/?LinkId=246307).  
  
 Dieser Fehler tritt meist dann auf, wenn [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] große Datenmengen zwischenspeichert oder wenn mehrere speicherintensive Prozesse ausgeführt werden.  
  
 Die folgenden Szenarien umfassen das Zwischenspeichern großer Datenmengen. Normalerweise können Sie diese Probleme beheben, indem Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] neu starten.  
  
-   Erstmalige Ausführung von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nach der Installation  
  
-   Installieren oder Deinstallieren einer Erweiterung  
  
-   Auswählen oder Anpassen von Elementen im **Werkzeugkasten**  
  
-   Ändern der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Einstellungen  
  
-   Wechsel des Systems in den Energiesparmodus \(Ruhezustand\), während [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] geöffnet ist  
  
 In den folgenden Szenarien ist viel aktiver Arbeitsspeicher erforderlich.  In diesen Fällen wird empfohlen, beim Ausführen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nur die wichtigsten Komponenten geöffnet zu haben oder zusätzliche Prozesse in einer zweiten Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auszuführen.  
  
-   Erstellen großer Projektmappen  
  
-   Arbeiten mit großen XML\-Dokumenten  
  
-   Durchführen von Upgrades von Projektmappen von einer früheren Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
-   Neuzuweisung von Projektmappen  
  
-   Ausführen von [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] während der Codebearbeitung  
  
-   Ausführen von IntelliTrace für mehrere Projekte  
  
 Wenn durch diese Maßnahmen der Fehler nicht vermieden werden kann, können Sie den verfügbaren Adressraum auf einem System, auf dem [!INCLUDE[win7](../debugger/includes/win7_md.md)] ausgeführt wird, vergrößern, wenn Sie "bcedit.exe" mit der folgenden Syntax ausführen:  
  
 **bcdedit \/set IncreaseUserVa 3072**  
  
 Durch diesen Befehl wird die virtuelle Speicherbelegung im Benutzermodus auf einem x86\-basierten System von 2 GB auf 3 GB erhöht.  Durch Hinzufügen des \/3GB\-Schalters kann das gesamte System mehr Arbeitsspeicher adressieren und jeder Anwendung einen höheren Prozentsatz des verfügbaren Arbeitsspeichers zuteilen.  
  
> [!NOTE]
>  Sie müssen "bcdedit.exe" mit Administratorberechtigungen ausführen.  Wenn die BitLocker\-Verschlüsselung aktiviert ist, müssen Sie sie zuerst anhalten, die Änderungen vornehmen, das System neu starten und BitLocker dann erneut aktivieren.  
  
 Selbst nachdem Sie die virtuelle Speicherbelegung auf 3 GB erhöht haben, kann der Fehler erneut auftreten, da jede einzelne Anwendung nach wie vor nur 2 GB virtuellen Speicher verwenden kann.  Wenn dieser Fehler weiterhin angezeigt wird, verringern Sie die Größe der Projektmappe, und starten Sie dann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] neu.  Sie können die Größe der Projektmappe reduzieren, indem Sie entweder Projekte entfernen, die selten verwendet werden, oder indem Sie Projekte entladen, die nicht benötigt werden.  Wenn der Fehler auftritt, wenn Sie Ihre Projektmappe erstellen, versuchen Sie, diese über eine Eingabeaufforderung zu erstellen.  
  
## Siehe auch  
 [Resources for Troubleshooting IDE Errors](../ide/reference/resources-for-troubleshooting-integrated-development-environment-errors.md)