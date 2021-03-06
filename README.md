# Linux VM Notes

## Contents

1. [Fundamentals][fundamentals] - Overview of virtual memory concepts without
   referencing any actual code or making assumptions about prior knowledge.

2. [Page Tables][page-tables] - Discussion about what [page tables][page-table]
   are, how they are used in linux, how they are manually traversed, the TLB and
   finally how page tables are allocated and freed.

3. [Process Address Space][process] - Discussion about virtual memory address
  space for processes - managing VMAs, process data structure
  construction/destruction, file/device-backed memory regions, page faulting,
  demand allocation, COW pages, copying to/from userland. __WORK IN PROGRESS__

4. [Transparent Huge Pages][trans-huge-pages] - Discussion about the kernel's
   [transparent huge pages][transhuge] functionality. __WORK IN PROGRESS__

5. [Out of Memory Killer][oom] - Discussion about overcommit and how the OOM
   killer selects and kills victims.

6. [Process Autopsy][autopsy] - Examining the memory allocation performed by the
   kernel for a simple userland application. __WORK IN PROGRESS__

### Function Cheat Sheets

1. [General Functions][funcs] - A list of general functions that don't fit under
   any other category.

2. [Page Table Functions][page-table-funcs] - Functions relating to
   [page tables][page-tables] (other than the copious functions relating to page
   table flags which rendered this page too huge.)

3. [Page Table Flag Functions][page-table-flag-funcs] - Functions relating to
   page table flags, separated out to avoid the page table functions page
   getting too huge.

4. [VMA Functions][vma-funcs] - Functions relating to memory descriptors and
   Virtual Memory Areas (VMAs), which are described in the
   [Process Address Space][process] section.

### Forthcoming

* [Physical Pages][physical] - Discussion about how physical pages are managed
  in linux.

* [Buddy Allocator][buddy] - Discussion about the fundamental underlying
  physical memory allocator.

* [Slab Allocator][slab] - Discussion about the object allocator.

* [cgroup Memory Management][cgroup] - Discussion about cgroup memory management
  functionality.

## Introduction

__NOTE:__ I target [linux 4.6][linux-4.6] and an x86-64 non-[NUMA][numa] system.

This repo contains my notes on the linux 4.6 VM subsystem. I don't make any
claim to their quality or usefulness.

This work first originated from the [notes][linux-gorman] I took from the
excellent [Understanding the Linux Virtual Memory Manager][amazon-gorman] by
[Mel Gorman][gorman] which, while great, targets the 2.4.22 kernel (released in
2003.) The obvious next stage of study was to take notes for a recent kernel,
which is what these notes are!

I am specifically targeting the 4.6 kernel since it was the mainline version at
the time of writing and should remain a sane and stable basis for notes and
hacks for the foreseeable future. I may update to newer kernel versions over
time depending on whether it makes sense to do so (and if I succeed at this
project of course!)

## Hacks

Speaking of hacks `linux-vm-notes`'s sister repo, [linux-vm-hacks][vm-hacks], is
where I'm putting exploratory code and patches relating to my exploration of the
VM subsystem.

## License

These notes are licensed under [Creative Commons BY-NC-SA][license].

[amazon-gorman]:http://www.amazon.co.uk/Understanding-Virtual-Memory-Manager-Perens/dp/0131453483
[gorman]:http://www.csn.ul.ie/~mel/blog/
[license]:http://creativecommons.org/licenses/by-nc-sa/4.0/
[linux-4.6]:https://github.com/torvalds/linux/tree/v4.6
[linux-gorman]:https://github.com/lorenzo-stoakes/linux-gorman-book-notes
[numa]:https://en.wikipedia.org/wiki/Non-uniform_memory_access
[page-table]:https://en.wikipedia.org/wiki/Page_table
[transhuge]:https://github.com/torvalds/linux/blob/v4.6/Documentation/vm/transhuge.txt
[vm-hacks]:https://github.com/lorenzo-stoakes/linux-vm-hacks

[autopsy]:sections/autopsy.md
[buddy]:sections/buddy.md
[cgroup]:sections/cgroup.md
[fundamentals]:sections/fundamentals.md
[trans-huge-pages]:sections/trans-huge-pages.md
[oom]:sections/oom.md
[page-tables]:sections/page-tables.md
[physical]:sections/physical.md
[process]:sections/process.md
[slab]:sections/slab.md

[funcs]:funcs/funcs.md
[page-table-flag-funcs]:funcs/page-table-flag-funcs.md
[page-table-funcs]:funcs/page-table-funcs.md
[vma-funcs]:funcs/vma-funcs.md
