<script setup>
import AdminLayout from "@/Layouts/AdminLayout.vue";
import { Head ,Link} from '@inertiajs/vue3';
import Table from '@/Components/UserTable.vue';
import TableRow from '@/Components/UserTableRow.vue';
import TableHeaderCell from '@/Components/UserTableHeaderCell.vue';
import TableDataCell from '@/Components/UserTableDataCell.vue';
defineProps(['users'])

</script>

<template>
    <Head title="Dashboard" />

    <AdminLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 dark:text-gray-200 leading-tight">Dashboard</h2>
        </template>

        <div class="max-w-7xl mx-auto py-4">
            <div class="flex justify-between">
                <h1>Users Index Page</h1>
                <Link :href="route('users.create')" class="px-3 py-2 text-white bg-indigo-500 hover:bg-indigo-700 rounded">
                    New User
                </Link>
            </div>

        </div>
        <div class="mt-6">
            <Table>
                <template #header>
                    <TableRow>
                        <TableHeaderCell>Id</TableHeaderCell>
                        <TableHeaderCell>Name</TableHeaderCell>
                        <TableHeaderCell>email</TableHeaderCell>
                        <TableHeaderCell>Action</TableHeaderCell>
                    </TableRow>
                </template>
                <template #default>
                    <TableRow v-for="user in users" :key="user.id">
                        <TableDataCell>{{user.id}}</TableDataCell>
                        <TableDataCell>{{user.name}}</TableDataCell>
                        <TableDataCell>{{user.email}}</TableDataCell>
                        <TableDataCell class="space-x-4">
                            <Link :href="route('users.edit',user.id)" class="text-green-400 hover:text-green-600">
                                Edit
                            </Link>
                            <Link :href="route('users.destroy',user.id)" method="DELETE" as="button" class="text-red-400 hover:text-red-600">
                                Delete
                            </Link>
                        </TableDataCell>
                    </TableRow>
                </template>
            </Table>
        </div>
    </AdminLayout>
</template>
