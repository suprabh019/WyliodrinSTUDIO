<template>
	<v-card class="disconnect">
		<v-tooltip top>
			<template v-slot:activator="{ on }">
				<v-btn @click.stop="disconnect" ref="fn" class="icon-btn" v-on="on">
					<img src="plugins/devices/wyapp/plugin/data/img/icons/disconnect-icon.svg" :alt="$t('DEVICE_WYAPP_DISCONNECT')" class="s24">
				</v-btn>
			</template>
			<span>{{$t('DEVICE_WYAPP_DISCONNECT')}}</span>
		</v-tooltip>
		<v-tooltip top>
			<template v-slot:activator="{ on }">
				<v-btn @click.stop="disconnectAndReboot" class="icon-btn" v-on="on">
					<img src="plugins/devices/wyapp/plugin/data/img/icons/restart-icon.svg" :alt="$t('DEVICE_WYAPP_RESTART')" class="s24">
				</v-btn>
			</template>
			<span>{{$t('DEVICE_WYAPP_RESTART')}}</span>
		</v-tooltip>
		<v-tooltip top>
			<template v-slot:activator="{ on }">
				<v-btn @click.stop="disconnectAndPowerOff" class="icon-btn" v-on="on">
					<img src="plugins/devices/wyapp/plugin/data/img/icons/turn-off-icon.svg" :alt="$t('DEVICE_WYAPP_TURNOFF')" class="s24">
				</v-btn>
			</template>
			<span>{{$t('DEVICE_WYAPP_TURNOFF')}}</span>
		</v-tooltip>
	</v-card>
</template>

<script>
export default {
	name: 'DisconnectDialog',
	mounted ()
	{
		this.$nextTick (() => {
			this.$refs.fn.$el.focus ();
		});
	},
	methods: {
		esc ()
		{
			this.$root.$emit ('submit');
		},
		disconnectAndReboot ()
		{
			this.$root.$emit ('submit', {
				disconnect: 'reboot'
			});
		},
		disconnectAndPowerOff ()
		{
			this.$root.$emit ('submit', {
				disconnect: 'poweroff'
			});
		},
		disconnect ()
		{
			this.$root.$emit ('submit', {
				disconnect: 'disconnect'
			});
		}
	}
};
</script>

<style lang="less" scoped>
	@import '../style/device.less';
</style>