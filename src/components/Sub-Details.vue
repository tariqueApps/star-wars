<template>
	<div>
		<v-flex v-for="attribute in attributes" :key="subDetails[attribute]">
			<v-card>
				<v-list>
					<v-subheader>{{ attribute | readableFormat }}</v-subheader>
					<v-list-tile>
						<v-list-tile-action>
							<v-icon v-if="subDetails[attribute]" color="black">star</v-icon>
						</v-list-tile-action>

						<v-list-tile-content>
							<v-list-tile-title
								v-text="subDetails[attribute]"
							></v-list-tile-title>
						</v-list-tile-content>
					</v-list-tile>
				</v-list>
			</v-card>
		</v-flex>
	</div>
</template>
<script>
export default {
  name: 'SubDetails',
  props: ['subDetails'],
  data() {
    return {
    }
  },
  computed: {
    attributes() {
      return this.subDetails ? Object.keys(this.subDetails).filter(item =>
        item === 'name'
        || item === 'climate'
        || item === 'rotation_period'
        || item === 'gravity'
        || item === 'diameter'
        || item === 'surface_water'
        || item === 'orbital_period') : [];
    }
  },
  filters: {
    readableFormat: function (value) {
      const str = value.replace('_', ' ');
      return str.charAt(0).toUpperCase() + str.slice(1);
    }
  }
};
</script>

