# adelie-kaslr-upgrade
Adelie's kernel upgrade  

# pie-v11 partial
https://patchwork.kernel.org/project/linux-hardening/cover/20200228000105.165012-1-thgarnie@chromium.org/  

# pie-v9
https://lore.kernel.org/all/201908050952.BC1F7C3@keescook/t/  

# linux-latest
stable: 6.7.6  
mainline: 6.8-rc5

# our successful testing
stable: 6.7.4  
mainline: -

# kernel archives
https://kernel.org/  

arch/x86/kernel/ftrace.c:146:6: error: implicit declaration of function 'probe_kernel_read' is invalid in C99 [-Werror,-Wimplicit-function-declaration]
        if (probe_kernel_read(replaced, (void *)ip, sizeof(replaced))) {
            ^
arch/x86/kernel/ftrace.c:146:6: note: did you mean '__kernel_read'?
./include/linux/fs.h:2919:9: note: '__kernel_read' declared here
ssize_t __kernel_read(struct file *file, void *buf, size_t count, loff_t *pos);
        ^
arch/x86/kernel/ftrace.c:160:19: error: use of undeclared identifier 'ideal_nops'
        memset(replaced, ideal_nops[1][0], sizeof(replaced));
                         ^
arch/x86/kernel/ftrace.c:163:7: error: implicit declaration of function 'text_ip_addr' is invalid in C99 [-Werror,-Wimplicit-function-declaration]
        ip = text_ip_addr(ip);
             ^
arch/x86/kernel/ftrace.c:165:6: error: implicit declaration of function 'probe_kernel_write' is invalid in C99 [-Werror,-Wimplicit-function-declaration]
        if (probe_kernel_write((void *)ip, replaced, sizeof(replaced)))
            ^
arch/x86/kernel/ftrace.c:165:6: note: did you mean 'probe_kernel_read'?
arch/x86/kernel/ftrace.c:146:6: note: 'probe_kernel_read' declared here
        if (probe_kernel_read(replaced, (void *)ip, sizeof(replaced))) {
            ^
4 errors generated.
make[4]: *** [scripts/Makefile.build:243: arch/x86/kernel/ftrace.o] Error 1
make[3]: *** [scripts/Makefile.build:481: arch/x86/kernel] Error 2
make[2]: *** [scripts/Makefile.build:481: arch/x86] Error 2

