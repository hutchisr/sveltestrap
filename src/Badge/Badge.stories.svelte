<script context="module">
  import Badge from './Badge.svelte';

  export const meta = {
    title: 'Stories/Badges',
    component: Badge,
    parameters: {
      controls: {
        exclude: /^(default)$/g
      }
    },
    argTypes: {
      class: {
        control: false,
        table: {
          disable: true
        }
      },
      children: {
        control: ''
      },
      color: {
        control: {
          type: 'select'
        },
        options: ['primary', 'secondary', 'success', 'danger', 'warning', 'info', 'light', 'dark']
      },
      href: {
        control: ''
      },
      pill: {
        control: 'boolean'
      },
      'default ': {
        description: 'This is the default content slot.',
        table: {
          category: 'slots',
          type: {
            summary: 'any'
          },
          defaultValue: {
            summary: 'empty'
          }
        }
      }
    },
    args: {
      class: '',
      children: '',
      color: 'primary',
      href: '',
      pill: false
    }
  };
</script>

<script>
  import { Story, Template } from '@storybook/addon-svelte-csf';
  import { Button } from '@sveltestrap/sveltestrap';

  const colors = ['primary', 'secondary', 'success', 'danger', 'warning', 'info', 'light', 'dark'];

  let isOpen = true;
  let toggle = () => (isOpen = !isOpen);
</script>

<Template let:args>
  <Badge {...args} />
</Template>

<Story name="Basic" args={{ color: 'primary', children: 'Badge' }} />

<Story name="Colors">
  <div class="horizontal">
    {#each colors as color}
      <Badge {color}>{color}</Badge>
    {/each}
  </div>
</Story>

<Story name="Buttons">
  <div class="horizontal">
    <Button color="primary">
      Notifications
      <Badge color="dark">4</Badge>
    </Button>

    <Button color="primary" outline>
      Notifications
      <Badge color="primary">7</Badge>
    </Button>
  </div>
</Story>

<Story name="Positioned">
  <div class="mb-3">
    <Button color="primary" class="position-relative">
      Inbox <Badge color="danger" pill class="position-absolute top-0 start-100 translate-middle"
        >100+
        <span class="visually-hidden">Unread messages</span>
      </Badge>
    </Button>
  </div>
  <div>
    <Button color="primary" class="position-relative">
      Profile <Badge color="danger" pill class="position-absolute top-0 start-100 translate-middle p-2 border">
        <span class="visually-hidden">New alerts</span>
      </Badge>
    </Button>
  </div>
</Story>

<Story name="Pills">
  <div class="horizontal">
    {#each colors as color}
      <Badge pill {color}>{color}</Badge>
    {/each}
  </div>
</Story>

<Story name="Links">
  <Badge href="https://svelte.dev" color="primary">Link Badge</Badge>
</Story>

<Story name="Headings">
  <div class="headings-example">
    <h1>Example heading <Badge color="secondary">New</Badge></h1>
    <h2>Example heading <Badge color="secondary">New</Badge></h2>
    <h3>Example heading <Badge color="secondary">New</Badge></h3>
    <h4>Example heading <Badge color="secondary">New</Badge></h4>
    <h5>Example heading <Badge color="secondary">New</Badge></h5>
    <h6>Example heading <Badge color="secondary">New</Badge></h6>
  </div>
</Story>
