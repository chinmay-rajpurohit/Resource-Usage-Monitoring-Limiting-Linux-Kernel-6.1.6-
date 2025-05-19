This repository contains a patch for Linux Kernel 6.1.6 that adds support for tracking and limiting the resource usage of specific user-space processes.

🔧 Features
🧠 Resource Tracker: Monitors heap memory usage and number of open files for registered processes and their threads by extending task_struct.

🚫 Resource Limiter: Enforces user-defined limits on heap size and open files. Exceeding processes are automatically terminated with SIGKILL.

🔁 System Calls:

sys_register(pid, heap_limit, fd_limit) – Register a process for tracking and apply limits.

sys_fetch(pid, *heap_usage, *fd_count) – Retrieve real-time usage statistics.

sys_deregister(pid) – Remove a process from monitoring.

⚙️ How to Apply the Patch (Linux Kernel 6.1.6)

wget https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.1.6.tar.xz
tar -xf linux-6.1.6.tar.xz
cd linux-6.1.6
patch -p1 < /path/to/your_patch_file.patch
make defconfig
make -j$(nproc)
sudo make modules_install
sudo make install
reboot


🧪 Testing
Build and boot into the patched kernel, then use simple user-space programs to test the custom system calls.
