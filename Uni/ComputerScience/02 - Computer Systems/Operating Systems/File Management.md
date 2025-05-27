File: Logical storage unit with attributes like name, type, size and permissions.
Operations: Create, read, write, delete, open (load metadata to memory), and close (update disk).
File types are identified by extensions, e.g., .exe for executable and .txt for text.
File structure: ranges from unstructured (byte structures) to complex (formatted documents)

# File Access Methods
- Sequential access: read/write sequentially (e.g., tapes)
- Direct Access: Random access using block numbers (e.g., disks).
- Indexed Access: Uses indexes for efficient lookup (e.g., databases).

# Directory Structures
- Single-Level: All files in one directory; prone to naming conflicts.
- Two-level Per-user directories; avoids naming issues but lacks grouping.
- Tree-Structured: Hierarchical; supports grouping and flexible naming.

# File Sharing and Security
- Sharing: Enabled via user/group permissions
- Protection: controls read/write.execute access for owners, groups, and public.