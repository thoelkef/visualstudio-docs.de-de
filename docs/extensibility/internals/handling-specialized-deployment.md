---
title: "Behandlung spezielle Bereitstellung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Bereitstellen von Anwendungen [Visual Studio SDK]"
  - "spezielle Bereitstellung"
ms.assetid: de068b6a-e806-45f0-9dec-2458fbb486f7
caps.latest.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 32
---
# Behandlung spezielle Bereitstellung
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Eine Bereitstellung ist ein optionaler Vorgang für Projekte.  Ein Webprojekt eine Bereitstellung unterstützt, z. B. ein Projekt aktualisieren zu lassen ein Webserver.  Entsprechend unterstützt ein **Intelligentes Gerät** Projekt eine Bereitstellung, um eine aufgebaute Anwendung für das Zielgerät zu kopieren.  Projekt untertypen können spezielle Verhalten der Bereitstellung angeben, indem sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>\-Schnittstelle implementieren.  Diese Schnittstelle definiert einen vollständigen Satz der Bereitstellung Vorgänge:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.AdviseDeployStatusCallback%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Commit%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStartDeploy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStatusDeploy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Rollback%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StartDeploy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StopDeploy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.UnadviseDeployStatusCallback%2A>  
  
 Der tatsächliche Bereitstellungsvorgang sollte in separaten Thread ausgeführt werden, um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] reagiert auch die Benutzerinteraktion auszuführen.  Die Methoden, die von <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> bereitgestellt werden, werden durch [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] asynchron aufgerufen und im Hintergrund ausgeführt werden und ermöglicht der Umgebung, um den Fortschritt eines Vorgangs Bereitstellung jederzeit abfragen oder den Vorgang zu beenden, ggf. an.  Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>\-Schnittstellen für Vorgänge werden von der Umgebung aufgerufen, wenn der Benutzer den Befehl zum Bereitstellen auswählen.  
  
 Um die Umgebung zu benachrichtigen, dass ein Bereitstellungsvorgang gestartet oder beendet wurde, muss der untertyp Projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback.OnStartDeploy%2A> und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback.OnEndDeploy%2A>\-Methoden aufrufen.  
  
## Spezialisierte Bereitstellung behandeln  
  
#### So erstellen Sie eine spezielle Behandlung Projekt ein Untertyp von Bereitstellung  
  
-   Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.AdviseDeployStatusCallback%2A>\-Methode die Umgebung zu registrieren, um Benachrichtigungen über den Status von Ereignissen zu empfangen.  
  
    ```vb#  
    Private adviseSink As Microsoft.VisualStudio.Shell.EventSinkCollection = New Microsoft.VisualStudio.Shell.EventSinkCollection()  
    Public Function AdviseDeployStatusCallback(ByVal pIVsDeployStatusCallback As IVsDeployStatusCallback, _  
                                               ByRef pdwCookie As UInteger) As Integer  
  
        If pIVsDeployStatusCallback Is Nothing Then  
            Throw New ArgumentNullException("pIVsDeployStatusCallback")  
        End If  
  
        pdwCookie = adviseSink.Add(pIVsDeployStatusCallback)  
        Return VSConstants.S_OK  
  
    End Function  
    ```  
  
    ```c#  
    private Microsoft.VisualStudio.Shell.EventSinkCollection adviseSink = new Microsoft.VisualStudio.Shell.EventSinkCollection();  
    public int AdviseDeployStatusCallback(IVsDeployStatusCallback pIVsDeployStatusCallback,   
                                          out uint pdwCookie)  
    {  
        if (pIVsDeployStatusCallback == null)  
            throw new ArgumentNullException("pIVsDeployStatusCallback");  
  
        pdwCookie = adviseSink.Add(pIVsDeployStatusCallback);  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.UnadviseDeployStatusCallback%2A>\-Methode, um die Registrierung der Umgebung abzubrechen, um Benachrichtigungen über den Status von Ereignissen zu empfangen.  
  
    ```vb#  
    Public Function UnadviseDeployStatusCallback(ByVal dwCookie As UInteger) As Integer  
        adviseSink.RemoveAt(dwCookie)  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```c#  
    public int UnadviseDeployStatusCallback(uint dwCookie)  
    {  
        adviseSink.RemoveAt(dwCookie);  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Commit%2A>\-Methode, um das Commit bestimmten Vorgangs zur Anwendung auszuführen.  Diese Methode wird hauptsächlich für Datenbankbereitstellung veranschaulicht.  
  
    ```vb#  
    Public Function Commit(ByVal dwReserved As UInteger) As Integer  
        'Implement commit operation here.  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```c#  
    public int Commit(uint dwReserved)  
    {  
         //Implement commit operation here.  
         return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Rollback%2A>\-Methode verwendet, um einen Vorgang ein Rollback auszuführen.  Wenn diese Methode aufgerufen wird, muss das Bereitstellungsprojekt tun, was zu den Änderungen Zurücksetzung geeignet ist und den Stand des Projekts wieder her.  Diese Methode wird hauptsächlich für Datenbankbereitstellung veranschaulicht.  
  
    ```vb#  
    Public Function Commit(ByVal dwReserved As UInteger) As Integer  
        'Implement commit operation here.  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```c#  
    public int Rollback(uint dwReserved)  
    {  
        //Implement Rollback operation here.  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStartDeploy%2A>\-Methode, um zu bestimmen, ob ein Projekt in der Lage ist, einen Bereitstellungsvorgang zu starten.  
  
    ```vb#  
    Public Function QueryStartDeploy(ByVal dwOptions As UInteger, ByVal pfSupported As Integer(), ByVal pfReady As Integer()) As Integer  
        If Not pfSupported Is Nothing AndAlso pfSupported.Length > 0 Then  
            pfSupported(0) = 1  
        End If  
        If Not pfReady Is Nothing AndAlso pfReady.Length > 0 Then  
            pfReady(0) = 0  
            If Not deploymentThread Is Nothing AndAlso (Not deploymentThread.IsAlive) Then  
                pfReady(0) = 1  
            End If  
        End If  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```c#  
    public int QueryStartDeploy(uint dwOptions, int[] pfSupported, int[] pfReady)  
    {  
        if (pfSupported != null && pfSupported.Length >0)  
            pfSupported[0] = 1;  
        if (pfReady != null && pfReady.Length >0)  
        {  
            pfReady[0] = 0;  
            if (deploymentThread != null && !deploymentThread.IsAlive)  
                pfReady[0] = 1;  
        }  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStatusDeploy%2A>\-Methode, um zu bestimmen, ob ein Bereitstellungsvorgang erfolgreich abgeschlossen wurde.  
  
    ```vb#  
    Public Function QueryStatusDeploy(ByRef pfDeployDone As Integer) As Integer  
        pfDeployDone = 1  
        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then  
            pfDeployDone = 0  
        End If  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```c#  
    public int QueryStatusDeploy(out int pfDeployDone)  
    {  
        pfDeployDone = 1;  
        if (deploymentThread != null && deploymentThread.IsAlive)  
            pfDeployDone = 0;  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StartDeploy%2A>\-Methode einen Bereitstellungsvorgang in einem separaten Thread zu starten.  Fügen Sie den Code in die spezifische Bereitstellung der Anwendung in der `Deploy`\-Methode.  
  
    ```vb#  
    Public Function StartDeploy(ByVal pIVsOutputWindowPane As IVsOutputWindowPane, ByVal dwOptions As UInteger) As Integer  
        If pIVsOutputWindowPane Is Nothing Then  
            Throw New ArgumentNullException("pIVsOutputWindowPane")  
        End If  
  
        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then  
            Throw New NotSupportedException("Cannot start deployment operation when it is already started; Call QueryStartDeploy first")  
        End If  
  
        outputWindow = pIVsOutputWindowPane  
  
        ' Notify that deployment is about to begin and see if any user wants to cancel.  
        If (Not NotifyStart()) Then  
            Return VSConstants.E_ABORT  
        End If  
  
        operationCanceled = False  
  
        ' Create and start our thread  
        deploymentThread = New Thread(AddressOf Me.Deploy)  
        deploymentThread.Name = "Deployment Thread"  
        deploymentThread.Start()  
  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```c#  
    public int StartDeploy(IVsOutputWindowPane pIVsOutputWindowPane, uint dwOptions)  
    {  
        if (pIVsOutputWindowPane == null)  
            throw new ArgumentNullException("pIVsOutputWindowPane");  
  
        if (deploymentThread != null && deploymentThread.IsAlive)  
            throw new NotSupportedException("Cannot start deployment operation when it is already started; Call QueryStartDeploy first");  
  
        outputWindow = pIVsOutputWindowPane;  
  
        // Notify that deployment is about to begin and see if any user wants to cancel.  
        if (!NotifyStart())  
            return VSConstants.E_ABORT;  
  
        operationCanceled = false;  
  
        // Create and start our thread  
        deploymentThread = new Thread(new ThreadStart(this.Deploy));  
        deploymentThread.Name = "Deployment Thread";  
        deploymentThread.Start();  
  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StopDeploy%2A>\-Methode, um einen Bereitstellungsvorgang abzubrechen.  Diese Methode wird aufgerufen, wenn ein Benutzer auf die Schaltfläche **Abbrechen** während des Bereitstellungsprozesses drückt.  
  
    ```vb#  
    Public Function StopDeploy(ByVal fSync As Integer) As Integer  
        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then  
            Return VSConstants.S_OK  
        End If  
  
        outputWindow.OutputStringThreadSafe("Canceling deployment")  
        operationCanceled = True  
        If fSync <> 0 Then  
            ' Synchronous request, wait for the thread to terminate.  
            If (Not deploymentThread.Join(10000)) Then  
                Debug.Fail("Deployment thread did not terminate before the timeout, Aborting thread")  
                deploymentThread.Abort()  
            End If  
        End If  
  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```c#  
    public int StopDeploy(int fSync)  
    {  
        if (deploymentThread != null && deploymentThread.IsAlive)  
            return VSConstants.S_OK;  
  
        outputWindow.OutputStringThreadSafe("Canceling deployment");  
        operationCanceled = true;  
        if (fSync != 0)  
        {  
            // Synchronous request, wait for the thread to terminate.  
            if (!deploymentThread.Join(10000))  
            {  
                Debug.Fail("Deployment thread did not terminate before the timeout, Aborting thread");  
                deploymentThread.Abort();  
            }  
        }  
  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
> [!NOTE]
>  Alle Codebeispiele in diesem Thema bereitgestellt werden, sind Teil eines umfangreicheren Beispiels, [VSSDK\-Beispiele](../../misc/vssdk-samples.md).  
  
## Siehe auch  
 [Projekt\-Untertypen](../../extensibility/internals/project-subtypes.md)