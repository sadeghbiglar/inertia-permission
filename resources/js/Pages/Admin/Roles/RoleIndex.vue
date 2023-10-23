<script setup>
import AdminLayout from "@/Layouts/AdminLayout.vue";
import {Head, Link} from '@inertiajs/vue3';
import Table from "@/Components/UserTable.vue";
import TableHeaderCell from "@/Components/UserTableHeaderCell.vue";
import TableDataCell from "@/Components/UserTableDataCell.vue";
import TableRow from "@/Components/UserTableRow.vue";
defineProps(['roles'])

</script>

<template>
    <Head title="Dashboard" />

    <AdminLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 dark:text-gray-200 leading-tight">Dashboard</h2>
        </template>

        <div class="max-w-7xl mx-auto py-4">
            <h1>Roles Index Page</h1>
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
                    <TableRow v-for="role in roles" :key="role.id">
                        <TableDataCell>{{role.id}}</TableDataCell>
                        <TableDataCell>{{role.name}}</TableDataCell>
                        <TableDataCell class="space-x-4">
                            <Link :href="route('users.edit',role.id)" class="text-green-400 hover:text-green-600">
                                Edit
                            </Link>
                            <Link :href="route('users.destroy',role.id)" method="DELETE" as="button" class="text-red-400 hover:text-red-600">
                                Delete
                            </Link>
                        </TableDataCell>
                    </TableRow>
                </template>
            </Table>
        </div>
    </AdminLayout>
</template>
