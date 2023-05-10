# Blender 3.4.1, Commit date: 2022-12-19 17:00, Hash 55485cb379f7

# backtrace
Exception Record:

ExceptionCode         : EXCEPTION_ACCESS_VIOLATION
Exception Address     : 0x00007FF7B22A757A
Exception Module      : blender.exe
Exception Flags       : 0x00000000
Exception Parameters  : 0x2
	Parameters[0] : 0x0000000000000001
	Parameters[1] : 0x000000000000006C


Stack trace:
blender.exe         :0x00007FF7B22A74A0  BKE_blendfile_link
blender.exe         :0x00007FF7ACA7ED80  bpy_lib_exit
python310.dll       :0x00007FFDF18EFDB0  PyCFunction_GetFlags
python310.dll       :0x00007FFDF18AB6C0  PyObject_MakeTpCall
python310.dll       :0x00007FFDF19C06B0  PyEval_GetFuncDesc
python310.dll       :0x00007FFDF19BA000  PyEval_EvalFrameDefault
python310.dll       :0x00007FFDF19BA000  PyEval_EvalFrameDefault
python310.dll       :0x00007FFDF19B9D90  PyEval_EvalCode
python310.dll       :0x00007FFDF19AAEE0  PyWarnings_Init
python310.dll       :0x00007FFDF18EFDB0  PyCFunction_GetFlags
python310.dll       :0x00007FFDF19B8450  PyOS_URandomNonblock
python310.dll       :0x00007FFDF19C06B0  PyEval_GetFuncDesc
python310.dll       :0x00007FFDF19BA000  PyEval_EvalFrameDefault
python310.dll       :0x00007FFDF19BA000  PyEval_EvalFrameDefault
python310.dll       :0x00007FFDF1A31DC0  PyRun_FileExFlags
python310.dll       :0x00007FFDF1A31DC0  PyRun_FileExFlags
python310.dll       :0x00007FFDF1A31C20  PyRun_StringFlags
blender.exe         :0x00007FF7ACA658E0  python_script_exec
blender.exe         :0x00007FF7ACA654B0  BPY_run_filepath
blender.exe         :0x00007FF7AB76A240  arg_handle_python_file_run
blender.exe         :0x00007FF7B2067CE0  BLI_args_parse
blender.exe         :0x00007FF7AB767FE0  main
blender.exe         :0x00007FF7B229EF70  __scrt_common_main_seh
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Threads:
Thread : 00001024
ntdll.dll           :0x00007FFE569B0AC0  ZwWaitForWorkViaWorkerFactory
ntdll.dll           :0x00007FFE569626D0  TpReleaseCleanupGroupMembers
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 00002c08
ntdll.dll           :0x00007FFE569B0AC0  ZwWaitForWorkViaWorkerFactory
ntdll.dll           :0x00007FFE569626D0  TpReleaseCleanupGroupMembers
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 00002644
ntdll.dll           :0x00007FFE569B0AC0  ZwWaitForWorkViaWorkerFactory
ntdll.dll           :0x00007FFE569626D0  TpReleaseCleanupGroupMembers
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 00002adc
ntdll.dll           :0x00007FFE569AD0D0  ZwWaitForSingleObject
KERNELBASE.dll      :0x00007FFE54322C90  WaitForSingleObjectEx
blender.exe         :0x00007FF7B26CD0B0  IlmThread_3_1::Semaphore::wait
blender.exe         :0x00007FF7B26CC8C0  IlmThread_3_1::ThreadPool::numThreads
blender.exe         :0x00007FF7AB92A910  std::thread::_Invoke<std::tuple<void (__cdecl usdBlender__pxrReserved__::HdRenderThread::*)(void) _
ucrtbase.dll        :0x00007FFE547F1B20  configthreadlocale
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 00003bb8
ntdll.dll           :0x00007FFE569AD0D0  ZwWaitForSingleObject
KERNELBASE.dll      :0x00007FFE54322C90  WaitForSingleObjectEx
blender.exe         :0x00007FF7B26CD0B0  IlmThread_3_1::Semaphore::wait
blender.exe         :0x00007FF7B26CC8C0  IlmThread_3_1::ThreadPool::numThreads
blender.exe         :0x00007FF7AB92A910  std::thread::_Invoke<std::tuple<void (__cdecl usdBlender__pxrReserved__::HdRenderThread::*)(void) _
ucrtbase.dll        :0x00007FFE547F1B20  configthreadlocale
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 00002f2c
ntdll.dll           :0x00007FFE569AD0D0  ZwWaitForSingleObject
KERNELBASE.dll      :0x00007FFE54322C90  WaitForSingleObjectEx
blender.exe         :0x00007FF7B26CD0B0  IlmThread_3_1::Semaphore::wait
blender.exe         :0x00007FF7B26CC8C0  IlmThread_3_1::ThreadPool::numThreads
blender.exe         :0x00007FF7AB92A910  std::thread::_Invoke<std::tuple<void (__cdecl usdBlender__pxrReserved__::HdRenderThread::*)(void) _
ucrtbase.dll        :0x00007FFE547F1B20  configthreadlocale
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 00002a1c
ntdll.dll           :0x00007FFE569AD0D0  ZwWaitForSingleObject
KERNELBASE.dll      :0x00007FFE54322C90  WaitForSingleObjectEx
blender.exe         :0x00007FF7B26CD0B0  IlmThread_3_1::Semaphore::wait
blender.exe         :0x00007FF7B26CC8C0  IlmThread_3_1::ThreadPool::numThreads
blender.exe         :0x00007FF7AB92A910  std::thread::_Invoke<std::tuple<void (__cdecl usdBlender__pxrReserved__::HdRenderThread::*)(void) _
ucrtbase.dll        :0x00007FFE547F1B20  configthreadlocale
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 000041bc
ntdll.dll           :0x00007FFE569AD0D0  ZwWaitForSingleObject
KERNELBASE.dll      :0x00007FFE54322C90  WaitForSingleObjectEx
blender.exe         :0x00007FF7B26CD0B0  IlmThread_3_1::Semaphore::wait
blender.exe         :0x00007FF7B26CC8C0  IlmThread_3_1::ThreadPool::numThreads
blender.exe         :0x00007FF7AB92A910  std::thread::_Invoke<std::tuple<void (__cdecl usdBlender__pxrReserved__::HdRenderThread::*)(void) _
ucrtbase.dll        :0x00007FFE547F1B20  configthreadlocale
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 00003fac
ntdll.dll           :0x00007FFE569AD0D0  ZwWaitForSingleObject
KERNELBASE.dll      :0x00007FFE54322C90  WaitForSingleObjectEx
blender.exe         :0x00007FF7B26CD0B0  IlmThread_3_1::Semaphore::wait
blender.exe         :0x00007FF7B26CC8C0  IlmThread_3_1::ThreadPool::numThreads
blender.exe         :0x00007FF7AB92A910  std::thread::_Invoke<std::tuple<void (__cdecl usdBlender__pxrReserved__::HdRenderThread::*)(void) _
ucrtbase.dll        :0x00007FFE547F1B20  configthreadlocale
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 000026bc
ntdll.dll           :0x00007FFE569AD0D0  ZwWaitForSingleObject
KERNELBASE.dll      :0x00007FFE54322C90  WaitForSingleObjectEx
blender.exe         :0x00007FF7B26CD0B0  IlmThread_3_1::Semaphore::wait
blender.exe         :0x00007FF7B26CC8C0  IlmThread_3_1::ThreadPool::numThreads
blender.exe         :0x00007FF7AB92A910  std::thread::_Invoke<std::tuple<void (__cdecl usdBlender__pxrReserved__::HdRenderThread::*)(void) _
ucrtbase.dll        :0x00007FFE547F1B20  configthreadlocale
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 000024a8
ntdll.dll           :0x00007FFE569AD0D0  ZwWaitForSingleObject
KERNELBASE.dll      :0x00007FFE54322C90  WaitForSingleObjectEx
blender.exe         :0x00007FF7B26CD0B0  IlmThread_3_1::Semaphore::wait
blender.exe         :0x00007FF7B26CC8C0  IlmThread_3_1::ThreadPool::numThreads
blender.exe         :0x00007FF7AB92A910  std::thread::_Invoke<std::tuple<void (__cdecl usdBlender__pxrReserved__::HdRenderThread::*)(void) _
ucrtbase.dll        :0x00007FFE547F1B20  configthreadlocale
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 00002198
ntdll.dll           :0x00007FFE569AD0D0  ZwWaitForSingleObject
KERNELBASE.dll      :0x00007FFE54322C90  WaitForSingleObjectEx
tbb.dll             :0x00007FFE427ED800  tbb::thread_bound_filter::try_process_item
tbb.dll             :0x00007FFE427ED800  tbb::thread_bound_filter::try_process_item
ucrtbase.dll        :0x00007FFE547F1B20  configthreadlocale
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 000002a0
ntdll.dll           :0x00007FFE569AD0D0  ZwWaitForSingleObject
KERNELBASE.dll      :0x00007FFE54322C90  WaitForSingleObjectEx
tbb.dll             :0x00007FFE427ED800  tbb::thread_bound_filter::try_process_item
tbb.dll             :0x00007FFE427ED800  tbb::thread_bound_filter::try_process_item
ucrtbase.dll        :0x00007FFE547F1B20  configthreadlocale
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 00000680
ntdll.dll           :0x00007FFE569AD0D0  ZwWaitForSingleObject
KERNELBASE.dll      :0x00007FFE54322C90  WaitForSingleObjectEx
tbb.dll             :0x00007FFE427ED800  tbb::thread_bound_filter::try_process_item
tbb.dll             :0x00007FFE427ED800  tbb::thread_bound_filter::try_process_item
ucrtbase.dll        :0x00007FFE547F1B20  configthreadlocale
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 00003500
ntdll.dll           :0x00007FFE569AD0D0  ZwWaitForSingleObject
KERNELBASE.dll      :0x00007FFE54322C90  WaitForSingleObjectEx
tbb.dll             :0x00007FFE427ED800  tbb::thread_bound_filter::try_process_item
tbb.dll             :0x00007FFE427ED800  tbb::thread_bound_filter::try_process_item
ucrtbase.dll        :0x00007FFE547F1B20  configthreadlocale
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 0000459c
ntdll.dll           :0x00007FFE569AD0D0  ZwWaitForSingleObject
KERNELBASE.dll      :0x00007FFE54322C90  WaitForSingleObjectEx
tbb.dll             :0x00007FFE427ED800  tbb::thread_bound_filter::try_process_item
tbb.dll             :0x00007FFE427ED800  tbb::thread_bound_filter::try_process_item
ucrtbase.dll        :0x00007FFE547F1B20  configthreadlocale
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 00001e7c
ntdll.dll           :0x00007FFE569AD0D0  ZwWaitForSingleObject
KERNELBASE.dll      :0x00007FFE54322C90  WaitForSingleObjectEx
tbb.dll             :0x00007FFE427ED800  tbb::thread_bound_filter::try_process_item
tbb.dll             :0x00007FFE427ED800  tbb::thread_bound_filter::try_process_item
ucrtbase.dll        :0x00007FFE547F1B20  configthreadlocale
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 00000480
ntdll.dll           :0x00007FFE569B0AC0  ZwWaitForWorkViaWorkerFactory
ntdll.dll           :0x00007FFE569626D0  TpReleaseCleanupGroupMembers
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 00002a24
ntdll.dll           :0x00007FFE569B0AC0  ZwWaitForWorkViaWorkerFactory
ntdll.dll           :0x00007FFE569626D0  TpReleaseCleanupGroupMembers
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Thread : 00002c58
ntdll.dll           :0x00007FFE569AD0D0  ZwWaitForSingleObject
KERNELBASE.dll      :0x00007FFE54322C90  WaitForSingleObjectEx
tbb.dll             :0x00007FFE427ED800  tbb::thread_bound_filter::try_process_item
tbb.dll             :0x00007FFE427ED800  tbb::thread_bound_filter::try_process_item
ucrtbase.dll        :0x00007FFE547F1B20  configthreadlocale
KERNEL32.DLL        :0x00007FFE552575F0  BaseThreadInitThunk
ntdll.dll           :0x00007FFE56962680  RtlUserThreadStart


Loaded Modules :
0x00007FF7AB5F0000 3.4.1.0              blender.exe C:\Program Files\Blender Foundation\Blender 3.4\blender.pdb 
0x00007FFE56910000 10.0.19041.2788      ntdll.dll  
0x00007FFE55240000 10.0.19041.2788      KERNEL32.DLL  
0x00007FFE54300000 10.0.19041.2788      KERNELBASE.dll  
0x0000000077110000 14.3.9014.6000       sysfer.dll  
0x00007FFE55D70000 10.0.19041.546       WS2_32.dll  
0x00007FFE54970000 10.0.19041.2846      RPCRT4.dll  
0x00007FFE36550000                      tbbmalloc.dll  
0x00007FFE56230000 10.0.19041.2788      USER32.dll  
0x00007FFE427E0000                      tbb.dll  
0x00007FFE54090000 10.0.19041.2846      win32u.dll  
0x00007FFE56530000 10.0.19041.2130      GDI32.dll  
0x00007FFE540C0000 10.0.19041.2788      gdi32full.dll  
0x00007FFE548D0000 10.0.19041.789       msvcp_win.dll  
0x00007FFE547D0000 10.0.19041.789       ucrtbase.dll  
0x00007FFE55E90000 10.0.19041.2130      ADVAPI32.dll  
0x00007FFE553A0000 7.0.19041.546        msvcrt.dll  
0x00007FFE55300000 10.0.19041.2846      sechost.dll  
0x00007FFE55600000 10.0.19041.2788      SHELL32.dll  
0x00007FFE503C0000 14.29.30139.0        VCRUNTIME140_1.dll  
0x00007FFE43BB0000 14.29.30139.0        VCRUNTIME140.dll  
0x00007FFE364C0000 14.29.30139.0        MSVCP140.dll  
0x00007FFE54CC0000 10.0.19041.2075      SHLWAPI.dll  
0x00007FFE541D0000 10.0.19041.1620      CFGMGR32.dll  
0x00007FFE54220000 10.0.19041.2486      bcrypt.dll  
0x00007FFE51D20000 10.0.19041.867       dbghelp.dll  
0x00007FFDFEA70000 6.1.0.0              sycl6.dll  
0x00007FFE554D0000 10.0.19041.1202      ole32.dll  
0x00007FFE17010000                      epoxy-0.dll  
0x00007FFE56560000 10.0.19041.2788      combase.dll  
0x00007FFDF4160000 9.0.0.0              openvdb.dll  
0x00007FFE568C0000 10.0.19041.546       PSAPI.DLL  
0x00007FFE55190000 10.0.19041.1865      shcore.dll  
0x00007FFDF1C70000 59.37.100.0          avcodec-59.dll  
0x00007FFE54C90000 10.0.19041.2673      IMM32.dll  
0x00007FFDC7990000                      cycles_kernel_oneapi_aot.dll  
0x00007FFDFE710000 59.27.100.0          avformat-59.dll  
0x00007FFE307C0000 59.7.100.0           avdevice-59.dll  
0x00007FFE54BC0000 10.0.19041.985       OLEAUT32.dll  
0x00007FFE0EDF0000 57.28.100.0          avutil-57.dll  
0x0000000067380000 1.1.0.0              libsndfile-1.dll  
0x00007FFE16F60000 6.7.100.0            swscale-6.dll  
0x00007FFDFE5D0000 1.21.1.0             OpenAL32.dll  
0x00007FFDFE470000 2.0.20.0             SDL2.dll  
0x000000006ACC0000                      libgmp-10.dll  
0x00007FFE472B0000                      libgmpxx.dll  
0x00007FFDF17A0000 3.10.8150.1013       python310.dll  
0x00007FFE54D20000 10.0.19041.2193      SETUPAPI.dll  
0x00007FFE48A50000                      tbbmalloc_proxy.dll  
0x00007FFE2C260000 10.0.19041.1         AVIFIL32.dll  
0x00007FFE3B1D0000 6.10.19041.1110      COMCTL32.dll  
0x00007FFE484B0000 10.0.19041.546       VERSION.dll  
0x0000000070680000                      libfftw3-3.dll  
0x00007FFE2C230000 4.7.100.0            swresample-4.dll  
0x00007FFE51870000 10.0.19041.746       dwmapi.dll  
0x00007FFE46E30000 10.0.19041.546       Secur32.dll  
0x00007FFE307A0000 10.0.19041.1         AVICAP32.dll  
0x00007FFE47130000 10.0.19041.546       WINMM.dll  
0x00007FFE2C200000 10.0.19041.1         MSVFW32.dll  
0x00007FFE49820000 10.0.19041.1         MSACM32.dll  
0x00007FFE53EE0000 10.0.19041.2130      SSPICLI.DLL  
0x00007FFE4AC20000 10.0.19041.1         winmmbase.dll  
0x00007FFE52700000 10.0.19041.546       kernel.appcore.dll  
0x00007FFE51F10000 10.0.19041.2788      windows.storage.dll  
0x00007FFE539A0000 10.0.19041.2788      Wldp.dll  
0x00007FFE53F60000 10.0.19041.844       profapi.dll  
0x00007FFE545E0000 10.0.19041.2486      bcryptPrimitives.dll  
0x00007FFE55DE0000 2001.12.10941.16384  clbcatq.dll  
0x00007FFE4D230000 10.0.19041.1503      MMDevApi.dll  
0x00007FFE53D20000 10.0.19041.1620      DEVOBJ.dll  
0x00007FFE4D410000 10.0.19041.2364      AUDIOSES.DLL  
0x00007FFE53DE0000 10.0.19041.546       powrprof.dll  
0x00007FFE53DC0000                      UMPDC.dll  
0x00007FFE538F0000 10.0.19041.546       CRYPTSP.dll  
0x00007FFE52F10000 10.0.19041.1052      rsaenh.dll  
0x00007FFE53910000 10.0.19041.546       CRYPTBASE.dll  

# Python backtrace
  File "D:\blendscript\code.txt", line 13 in <module>
  File "<string>", line 1 in <module>
