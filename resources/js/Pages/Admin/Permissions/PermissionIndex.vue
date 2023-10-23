<script setup>
import AdminLayout from "@/Layouts/AdminLayout.vue";
import {Head, Link} from '@inertiajs/vue3';
import Table from "@/Components/UserTable.vue";
import TableHeaderCell from "@/Components/UserTableHeaderCell.vue";
import TableDataCell from "@/Components/UserTableDataCell.vue";
import TableRow from "@/Components/UserTableRow.vue";
defineProps(['permissions'])
</script>

<template>
    <Head title="Dashboard" />

    <AdminLayout>
        <div class="max-w-7xl mx-auto py-4">
            <div class="flex justify-between">
                <h1>Permissions Index Page</h1>
                <Link :href="route('permissions.create')" class="px-3 py-2 text-white bg-indigo-500 hover:bg-indigo-700 rounded">
                    New Permission
                </Link>
            </div>

        </div>
        <div class="mt-6">
            <Table>
                <template #header>
                    <TableRow>
                        <TableHeaderCell>Id</TableHeaderCell>
                        <TableHeaderCell>Name</TableHeaderCell>
                        <TableHeaderCell>Action</TableHeaderCell>
                    </TableRow>
                </template>
                <template #default>
                    <TableRow v-for="permission in permissions" :key="permission.id">
                        <TableDataCell>{{permission.id}}</TableDataCell>
                        <TableDataCell>{{permission.name}}</TableDataCell>
                        <TableDataCell class="space-x-4">
                            <Link :href="route('permissions.edit',permission.id)" class="text-green-400 hover:text-green-600">
                                Edit
                            </Link>
                            <Link :href="route('permissions.destroy',permission.id)" method="DELETE" as="button" class="text-red-400 hover:text-red-600">
                                Delete
                            </Link>
                        </TableDataCell>
                    </TableRow>
                </template>
            </Table>
        </div>
    </AdminLayout>
</template>
